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
# Scaffolding
* erstellt eine Resource (Model) mit passenden Tabellen, Views, Controllern und REST Routen 

* `rails g scaffold attribute:type ...`
  * erstellt Datenbank Migration
  * erstellt Routen
  * erstellt Models
  * erstellt Erb Views
  * erstellt CRUD Controller

.notes CRUD Create, Update, Delete, REST => Darstellung von Resourcen via URLs und Anwendung der HTTP Verben um Aktionen anzugeben

!SLIDE
# Übung
  * Erstelle ein neue resource "BeamTarget" mit den attributen "density" & "volume"
  * Bonus: Im root Verzeichniss soll die Liste der Beam Targets zu sehen sein. (see routes.rb)
  * Test ob es funktioniert

!SLIDE
# Lösung
  * `rails g scaffold beam_target density:integer volume:integer`
  * `root :to => 'beam_targets#index'` in routes.rb

.notes walk through the code

!SLIDE
# Migration
  * DB unabhängige Schemaänderungen
  * in zwei Richtungen up & down
  * `rake db:create:all` Datenbank anlegen  
  * `rake db:migrate` um DB aufs neue Schema zu migrieren
  * Achtung! Abhägigkeiten vom App Code in Migrations vermeiden

.notes open db/migrations/???_create_beam_targets.rb

!SLIDE  
# Models
  * Persistenz via ActiveRecord::Base
  * Business Logik in der Model Datei
  * `rake g model name attribute:type`

.notes models/beam_target.rb öffnen als Beispiel

<!SLIDE small>
# Routen
  * stehen in `routes.rb`
  * Ordnet Requests Controllern und Actions zu
  * `resources :products` CRUD ressource
  * `match 'products/:id/purchase' => 'catalog#purchase', :as => :purchase` bennante Route mit parameter (purchase_url)

.notes config/routes.rb öffnen für weitere Beispiele

!SLIDE  
# Controller
  * `rails g controller name`
  * public Methoden sind Actions
  * standard Actions
    * index
    * new
    * edit
    * update
    * create
    * destroy

.notes öffne controller/beam_targets_controller.rb

<!SLIDE small>
# Views / ERB
  * HTML + Ruby (Embedded Ruby)
  * `<% @user.name %>` evaluiert ohne Output
  * `<%= @user.name %>` evaluiert und stellt Output da
  * CRUD views "new, edit, show, index"

.notes öffne views/beam_targets/show.html.erb, NEXT: git


