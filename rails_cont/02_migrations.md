!SLIDE
# Migrations
  * erstellen Tabellen/Indices/Constraints
  * Wichtige Methoden
    * create|change|drop|rename_table
    * add|change|remove|rename_column
    * add|remove_index

<!SLIDE>
# Uniqe index erstellen um Einzigartigkeit zu sichern

    @@@ ruby
    add_index :user, :email, :unique => true
    
  * Achtung! validates_uniqueness ist nicht aussreichend

.notes validation Problem: Nachdem die Prüfung durchgeführt wurde kann sich der Datenbankinhalt ändern

!SLIDE
# Übung
Erstelle eine neue Migration die eine Tabelle für User anlegt mit name, vorname und email, die email muss eindeutig sein. Siehe (http://api.rubyonrails.org/)
