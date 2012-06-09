!SLIDE
# Deployment

!SLIDE
![](../images/meme.jpg)

!SLIDE
# heroku
 * kostenlos! ein prozess
 * git push heroku
 * file system wird bei jedem deployment neu initialisiert
 * Mit nur einem Klick Services hinzufügen
 * einige Services müssen dazugekauft werden != free
 * Datenbank ist postgresql

.notes show heroku
 
!SLIDE
# appache + passenger
  * volle kontroller
  * auch kostenlos
  * DIY

!SLIDE
# passenger setup
  http://www.modrails.com/documentation/Users%20guide%20Apache.html#_configuring_phusion_passenger

!SLIDE
# deployment schritte
  * code auschecken
  * migrations laufen lassen
  * geteilte pfade neu verlinken
  * ggf. assets pre-compile
  * server / rails neu starten
  * was wenn was schief geht?

  



