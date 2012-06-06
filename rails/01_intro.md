!SLIDE center
# Rails

<!SLIDE small>
# Vorstellung 
 * Framework für Webanwendungen (verhalf Ruby zum Durchbruch)
 * Ruby On Rails wurde von 37signals' David Heinemeier Hansson (DHH) erdacht
 * July 2004: Erster OpenSource Release
 * > 2007: De-facto Standard für neue Startups in Silicon Valley ;)
 * Große Seiten mit Rails (twitter, github, shopify, Groupon)
 
!SLIDE
# Konzepte
  * Model View Controller Struktur
  * Opinionated => Erledigt Aufgaben auf eine Art
  * Konvention vor Konfiguration
  * DRY (Don't Repeat Yourself)
  * Test Driven Development
  * Multiple Enviroments
  
.notes Macht andere Rangehensweisen schwerer, Trennung von Presentation und Geschäftslogik, Prinzipen bauen auf einander auf

!SLIDE
# Model View Controller
  * Model: Geschäftslogic / Persistenz
  * Controller: Controll flow für den User, lädt benötigte Models
  * View: Anzeigelogik und Layout

!SLIDE
# Struktur
  * Ordner geben Struktur vor
  * /app QuellCode der Webanwendung
  * /app/models - Models
  * /app/controller - Controller
  * /app/views - Views

!SLIDE  
# Struktur (cont)  
  * /lib eigene Hilfsbibliotheken
  * /vendor 3rd Party Code
  * /config Konfiguration der Anwendung
  * /db Datenbankstruktur und Daten
  * /public statischer Content

!SLIDE
# Rails Komponenten
  * ActiveRecord : ORM
  * ActionController: Beantworten von Request mit richtigen Views and Daten (Routing)
  * ActionView: HTML Generieren
  * ActiveSupport: Hilfs und Support Funktionen 