!SLIDE center
# Git
distributed version control system

.notes http://git-scm.com/download, tar xvjf git-1.7.3.4.tar.bz2, ./configure, wget ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/Base:/build/standard/x86_64/zlib-devel-1.2.3-135.52.x86_64.rpm, sudo rpm -ivh zlib-devel-1.2.3-135.52.x86_64.rpm make && make install

!SLIDE
# Why git?
  * distributed means local history
  * easy branching / forking
  * github community

!SLIDE smaller
# Konzepte
  * die change history steht lokal zur verfügung
  * lokale commits können mit remotes geteilt werden (push)
  * entfernte änderungen können in die lokale history integriert werden (pull)
  * Stash als ort zum "zwischenlagern von änderungen"
  * flexibles branching Model,leichtes erstellen,löschen, mergen und teilen
  * Assoziation von lokalen mit remote Branches via Tracking
  
!SLIDE smaller
# Grundlagen
  * `git init path` - neues repo anlegen
  * `git commit path1 path2` - dateien in pfad committen
  * `git pull origin master` - remote history von master in den lokalen 
  * `git push origin master` - lokale history zu remote master branch
  * `git status` - geänderte/neue dateien anzeigen
  * `git diff filename` - diff der aktuellen Datei mit lokaler history
  * `git checkout branch` - in lokalen branch wechseln
  * `git checkout .` - nicht commitete Änderungen löschen