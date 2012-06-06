!SLIDE smaller
# Übung
* Wechsle in dein Projektverzeichnis mit dem Namen "rails-schulung". 
* Stelle sicher das du Ruby 1.9.3 verwendest.
* Erstelle ein neues gemset "rails-schulung".
* Installiere bundler und erstelle eine neue Gemfile für die aktuelle Rails version und dem mysql2 gem.
* installiere die gems der Gemfile
* Bonus: stell sicher das beim Wechsel in das Verzeichnis immer alles richtig geladen wird. (Stichwort: rvmrc)

!SLIDE smaller
# Lösung
  * `rvm use ruby-1.9.3@rails-schulung --create`
  * `gem install bunder`  
  * Gemfile

        @@@ ruby
        source 'https://rubygems.org'
        gem 'rails', '~> 3.2.5'
        gem 'mysql2'
  
  * `bundle install`
  
.notes lösung .rvmrc, beliebigen code ausführbar

