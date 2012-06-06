!SLIDE
# Verwendung
* `rails new` - Generator für Rails app
* `rails generate` - Generator für Scaffolds
* `rails server` - WebServer für Lokale Entwicklung
* `rake` - Erledigt alle Aufgaben wie Datenbank verwalten, Tests laufen lassen

.notes shortcutes, rake -T 

!SLIDE
# Übung
Erstelle eine neue Anwendung im Verzeichnis Rails Schulung. Die Rails Anwendung soll mysql verwenden und keine Dateien für TestUnit generieren. Prüfe ob die Anwendung läuft.

Hints: (rails new, rails server)

!SLIDE center
# Lösung
`rails new .  -T -d mysql`

!SLIDE
# Scafolding
* erstellt eine Resource (Model) mit passenden Tabellen, Views, Controllern und REST Routen 

* `rails g resource attribute:type ...`
  * erstellt Datenbank Migration
  * erstellt Routen
  * erstellt Models
  * erstellt Erb Views
  * erstellt CRUD Controller

.notes CRUD Create, Update, Delete, REST => Mapping der HTTP werben

!SLIDE
# Migration
  * `rake db:create:all` Datenbank anlegen
  * DB unabhängige Schemaänderungen
  * up/down
  * `rake db:migrate` für die DB anwenden
  * Achtung! Abhägigkeiten vom Code vermeiden
  
!SLIDE smaller
# Routen
  * stehen in `routes.rb`
  * Ordnet Requests Controllern und Actions zu
  * `resources :products` CRUD resource mit HTTP Verben
  * `match 'products/:id/purchase' => 'catalog#purchase', :as => :purchase` bennante Route mit parameter (purchase)

!SLIDE  
# Models
  * Persistenz und Business Logik
  * `rake g model name attribute:typ`

!SLIDE
# Erb Views
  * HTML + Ruby (Embedded Ruby)
  * `<% %>` evaluiert ohne output
  * `<%= %>` evaluiert und schreibt output
  * CRUD views "new, edit, show, index"

!SLIDE  
# Controller
  * `rails g controller name`
  * public Methoden sind Actions
  * CRUD Actions
    * index
    * new
    *
    
!SLIDE
# Übung
  * Erstelle ein neue resource "BeamTarget" mit den attributen "density" & "volume"
  * Im root Verzeichniss soll die Liste der Beam Targets zu sehen sein.
  * Test ob es funtioniert

!SLIDE
# Lösung
  * `rails g scaffold beam_target density:integer volume:integer`
  * `root :to => 'beam_targets#index'` in routes.rb

.notes walk through the code

!SLIDE  
# URL Helper

!SLIDE
# Forms
