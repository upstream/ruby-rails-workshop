!SLIDE center
# Ruby Infrastruktur

!SLIDE bullets
# IRB - Interaktive Ruby
* aka "ruby console"
* Interpretiert Ruby Zeile für Zeile
  * REPL: Read Eval Print Loop

!SLIDE
# ruby
* `ruby` ist der Ruby-Interpreter
* `ruby hallo.rb` führt die Ruby-Quelldatei `hallo.rb`
* wichtige Optionen
   * `-w` - Warnungen
   * `-v` - Version
   * `-c` - Syntax prüfen

!SLIDE
# gem

* aka RubyGems
* der Packetmanager für Ruby
* Ein gem ist eine library, ein Program oder ein Plugin
* `gem install foo` - lädt runter und installiert das "foo" gem von rubygems.org

!SLIDE
# rake
* Ruby Make
* gem das verwendet wird um verschiedenste Aufgaben zu automatisieren
* Aufgaben werden in einer "Rakefile" mit Ruby programmiert
* `rake -T` zeigt die verfügbaren Aufgaben

!SLIDE
# bundler

* Dependency Manager für Ruby
* gem Programm das Abhängigkeiten von gems in einer 'Gemfile' Datei verwaltet.
* Bsp: `gem 'rails', '~> 3.2.1'`
* installation mit `gem install bundler`

!SLIDE
# rvm 

* Programm das verschiedene Ruby Versionen und deren gems auf einem Computer verwaltet.
  * Verwendung
    * `rvm list`
    * `rvm install 1.9.2`
    * `rvm use 1.9.2`
  * Verwendung um gemsets zu verwalten
    * `rvm gemset create teaching`
    * `rvm use 1.9.2@teaching`
