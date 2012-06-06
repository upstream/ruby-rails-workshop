!SLIDE smaller
# Übung
  * Erstelle ein neues git Repository für das Projekt
  * Mache deinen ersten commit an
  * Lege ein Account auf GitHub an und erstelle dort das Projekt ebenfalls
  * Füge dein GitHub Projekt als remote hinzu
  * Pusche den commit zu GitHub
  * Bonus: Stelle dein Nutzername und email für git richtig ein
  
.notes ssh keys nicht vergessen (ggf ssh-keygen -t rsa)

!SLIDE smaller
# Lösung
  * `git init .`
  * `git add .`
  * `git commit -m 'initial commit'`
  * `git remote add origin https://github.com/thilo/rails-schulung.git`
  * `git push origin master`
  * Bonus: `git config --global user.name "Thilo Utke" && git config --global user.email thilo@upstre.am`
  