!SLIDE center
# Klassen und Instanzen

!SLIDE
# Instanzen erstellen

  `cookie = Cookie.new`

!SLIDE
# Konstruktor

* Um eine Instanz zu erstellen wir die `new` Methode auf der Klasse aufgerufen
* die `new` Methode ruft dann die `initialize` Methode auf der Instanz auf

        @@@ ruby
        class Cookie
          def initialize
            @chips = 0
          end          
        end

.notes 1. allocates memory for the instance 2. calls *initialize* on the new instance 3. returns a pointer to the instance

!SLIDE
# Instanz Methoden

    @@@ruby
    class Cookie
      def bake
        @temp = 350
      end
    end

!SLIDE  
# Getter und Setter Methoden

    @@@ ruby
    class Person
      def age=(years_old)
        @age = years_old
      end
      def age
        @age
      end
    end

    alice = Person.new
    alice.age= 17
    alice.age #=> 17

    alice.@age #=> SyntaxError

!SLIDE
# Ruby's Setter Sugar

`alice.age = 17`

ist gleich

`alice.age=(17)`

!SLIDE
# Das Setter Problem

Innerhalb des Objekts lassen sich Setter nicht einfach verwenden, Die Setter Methode sieht aus wie eine lokale Variablen Zuweisung

      @@@ruby
      class Person
        def age=(years_old)
          @age = years_old
        end
        def bar
          age = 13   # oops
        end
      end

!SLIDE
# Das Setter Problem Lösung: 

Methodenaufruf auf der aktuellen Instanz mit `self.age` oder direkt die Instanzvarialbe `@age` verwenden

      @@@ruby
      class Person
        def age=(years_old)
          @age = years_old
        end
        def bar
          @age = 13
        end
        def bat
          self.age = 13
        end
      end

.notes Immer darauf achten! Dieser Umstand wird oft vergessen

!SLIDE
# Attribute

Ein *Attribute* ist eine Instanzevariable mit entsprechenden Getter und Setter

    @@@ ruby
    class Person
      def age=(years_old)
        @age = years_old
      end
      def age
        @age
      end

!SLIDE
# Attribute Shortcuts

    @@@ ruby
    class Person
      #def age; @age; end
      attr_reader :age
      #def age=(x); @age = x; end
      attr_writer :age 
      # beides
      attr_accessor :age
    end
