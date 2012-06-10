!SLIDE

# Unit Testing

* testet eine Komponente: Methode/Klasse/Algorithmus
* viele Tests pro Konponente
* _one assertion per test_
* setup, code ausführen, assertions, teardown

.notes NEXT: übung

!SLIDE

# Übungen - Test First

Kleiner Tachenrechner, der jeweils 2 Zahlen miteinander verrechnet:

    @@@ ruby
    "2+2" = 4
    "1/3" = 0.33 # auf 2 Stellen runden
    "2/6" = 0.67
    "2*4" = 8
    "2^2" == 8
    ...

.notes NEXT: testcase

!SLIDE small

# Test

    @@@ ruby
    require 'minitest/unit'
    class CalculatorTest < Test::Unit::TestCase
      def setup
        @calculator = Calculator.new
      end

      def test_adds_numbers
        assert_equal 4, @calculator.execute("2+2")
      end
    end

!SLIDE

# Implementierung (z.B.)

    @@@ ruby
    class Calculator
      def execute(calculation)
        4
      end
    end

Nur soweit implementieren wie nötig (= bis Tests grün).

!SLIDE

# Edge cases

    @@@ ruby
    ""
    nil
    "1/0"


!SLIDE

# Mocking/Stubbing

!SLIDE

# Motivation

* mehrere Komponenten, z.B. Rails - Controller, Views, Models
* zusammen testen zu komplex: setup, zu langsam (z.B. Datenbank)
* Komponenten ersetzen durch stubs

!SLIDE

# Mocking

* Interaktion zwischen Komponenten testen
* externe Komponenten: z.B. Twitter API

.notes NEXT: mocks vs stubs

!SLIDE

# Mocks vs. Stubs

* Stubs: Objekt das sich verhält wie ein anderes; vorgeben, welcher Aufruf was zurückgibt
* Mocks: testen, ob bestimmte Aufrufe erfolgen und womit; vorgeben was passieren soll, wenn nicht Fehler

.notes NEXT: bsp.

!SLIDE small

# Beispiel ohne Mocks

    @@@ ruby
    class TestWithoutStubs < Test::Unit::TestCase
      def setup
        @twitter = TwitterClient.new 'freaklikeme', '***'
        @twitter.posts.each(&:destroy)
      end

      def test_returns_number_of_tweets
        @twitter.post 'a test post'
        @twitter.post 'another test post'

        assert_equal 2, @twitter.posts.size
      end
    end

.notes NEXT: problem dabei

!SLIDE

# Problem

* Twitter/Netzwerk kann down sein
* zu langsam (bei 2000 Tests)
* manche APIs kosten Geld (Payment-API)

!SLIDE small

# Beispiel mit Stubs

    @@@ ruby
    require 'mocha'

    class TestWithStubs < Test::Unit::TestCase
      def setup
        @twitter = TwitterClient.new '', ''
      end

      def test_returns_number_of_tweets
        @twitter.connection = stub(:connection,
          get_posts: [stub, stub])

        assert_equal 2, @twitter.posts.size
      end
    end

!SLIDE

# Vorteile

* schnell
* kein Netzwerk-Zugriff
* zuverlässig


!SLIDE

# Nachteil

* bekommt nicht mit, wenn sich Twitter-API oder `Connection` Objekt ändert.

!SLIDE

# Dependency Injection

Externe Komponenten ersetzen - wie?

!SLIDE small

# Setter

    @@@ ruby
    @object_under_test.dependency = stub(:dependency)

!SLIDE small

# Constructor

    @@@ ruby
    MyObject.new stub(:dependency)

!SLIDE small

# Dependency Constructor

    @@@ ruby
    class MyObject
      def initialize
        @dependency = Dependency.new 'blah'
      end
    end

    Dependency.stubs(:new).returns(stub(:dependency))

Sollte auch constructor-Argumente testen (mit mocks).

!SLIDE small

# Variable Injection

    @@@ ruby
    object = MyObject.new
    object.instance_variable_set(
      "@dependency", stub(:dependency))

Nachteil: Variablenname kann sich ändern.

!SLIDE

# Im Idealfall

Code so schreiben, dass dependency injection über public interface möglich ist.

!SLIDE

# Übung

Klasse `AdvancedCalculator`, `Calculator` als dependency.

    @@@ ruby
    assert_equal 15, "(3+3) + (3*3)"

* ein Test ohne stubs
* Tests mit stubs/mocks

.notes NEXT: testcase

!SLIDE small

    @@@ ruby
    class AdvancedCalculatorTest < Test::Unit::TestCase
      def setup
        @advanced_calc = AdvancedCalculator.new
        @calculator = Calculator.new
        @advanced_calc.calculator = @calculator
      end

.notes NEXT: code testcase

!SLIDE small

      @@@ ruby
      def test_delegates_to_calculator
        @calculator.expects(:execute).with("3+3")
        @calculator.expects(:execute).with("3*3")

        @advanced_calc.execute "(3+3) + (3*3)"
      end

.notes NEXT: code testcase

!SLIDE small

      @@@ ruby
      def test_combines_results
        @calculator.stubs(:execute).with(
          "3+3").returns(6)
        @calculator.stubs(:execute).with(
          "3*3").returns(9)

        @calculator.expects(:execute).with(
          "6+9")

        @advanced_calc.execute(
          "(3+3) + (3*3)")
      end

.notes NEXT: code testcase

!SLIDE small

      @@@ ruby
      def test_returns_results
        @calculator.stubs(:execute).with(
          "3+3").returns(6)
        @calculator.stubs(:execute).with(
          "3*3").returns(9)
        @calculator.stubs(:execute).with(
          "6+9").returns(15)

        assert_equal 15, @advanced_calc.
          execute("(3+3) + (3*3)")
      end
    end

# Refactoring

.notes NEXT: definition von refactoring

!SLIDE

## Code ändern, ohne seine Funktionen zu ändern.

!SLIDE

# Aufräumen.

!SLIDE

# Wartbarkeit

!SLIDE

# Angst?!

!SLIDE

* neue Ruby/Rails-Version
* Code in neue Klassen auslagern
* Methoden aufteilen
* `bundle update`

!SLIDE

# Ohne Tests? Srsly?