!SLIDE center
#Ruby

!SLIDE smaller
# Basis Syntax
* Constant/Classname
* method_name arg
* instance.method_name arg1, arg2
* "string"
* 1 (Integer)

.notes Um die Bsp zu verstehen

!SLIDE
# Eigenschaften
 * interpretiert
 * objektorientiert ( Java < Ruby  < smalltalk )
 * dynamisch

!SLIDE
# Bsp: interpretiert
  * `puts 'Hello World!'`
  * `eval 'puts "Hello World"'`

!SLIDE
# Bsp: objektorientiert
* `1.day.from_now`

.notes smalltalk isFalse, isTrue

!SLIDE
# Bsp: dynamisch
  * `a = 1; a = a + 1.0`
  * `['A', 1]`

!SLIDE
# Konzepte
  * Duck Typing
  * Principle of Least Surprise (For Matz)

!SLIDE
# Bsp: Duck Typing in Action
  * `"Hello".to_s`
  * `Object.to_s`
  * `"Hello"`
  * `Object`

.notes IRB calls to_s on each returned object

!SLIDE
# Bsp: Least Suprise
* `1 + 1 # => 2`
* `[1, 2] + [2, 3] # => [1, 2, 3, 4]`
* `"Hello " + "World" # => ?`
* `Time.now + 60 # => ?`


!SLIDE left
# Übung: 

Methode die zwei Zahlen oder Strings zu einem String verbindet. 

Methoden definieren:

    @@@ ruby
    def methodname arg1, arg2
      mach was
    end
!SLIDE
# Lösung

    @@@ ruby
    def join_to_sting first, second
      first.to_s + second.to_s
    end

!SLIDE bullets
# Widerholung
  * interpretiert
  * objektorientiert
    * `1.day.from_now`
  * dynamisch und Duck Typing
    * `first.to_s + second.to_s`



