!SLIDE
# Ruby Funktionen

# Expression values

In Ruby gibt jeder Ausdruck einen Wert zurück

    @@@ ruby
    >> 2 + 2
    => 4
    >> (2+2).zero?
    => false
    >> "zero" if (2+2).zero?
    => nil

# Funktionswerte

Der Wert einer Funktion ist der Wert des letzten Ausdrucks
(es seid den ein Wert wird an `return` übergeben)

# Parameter und Rückgabewerte

    @@@ ruby
    def to_fahrenheit(celcius)
      celcius * 9.0 / 5 + 32
    end

* `celcius` ist ein Parameter
* Der Rückgabewert ist das Ergebniss des Ausdrucks

.notes the keyword `return` is available, but usually unnecessary


# Splat Arguments
repräsentieren ein Array von Argumenten
    @@@ ruby
    def greet(greeting, *names)
      names.each do |name|
        puts "#{greeting}, #{name}!"
      end
    end

    >> greet("Hello", "Alice", "Bob", "Charlie")
    Hello, Alice!
    Hello, Bob!
    Hello, Charlie!

# Standardwerte

    @@@ ruby
    def eat(food = "chicken")
      puts "Yum, #{food}!"
    end

    >> eat
    Yum, chicken!

    >> eat "arugula"
    Yum, arugula!


# "options hash" Pattern

Um variable oder benannte Parameter zu übergeben wir ein einem Argument ein Hash übergeben

    @@@ruby
    bake("Rubylicious", :flour => "sour")
    bake("Rubynickel", :milk => "butter")
    
    def bake(name, options = {})
      flour = options[:flour] || "rye"
      milk = options[:milk] || "cream"
      puts "baking a nice #{flour} loaf with #{milk}"
    end

