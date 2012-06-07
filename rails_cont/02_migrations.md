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
Erweitere die Anwendung so das es Nutzer mit name, vorname und email (eindeutig). Siehe  gibt die die BeamTargets für bestimmte Tage buchen können. Kein BeamTarget darf am Tag zweimal gebucht werden.

<!SLIDE small>
# Lösung
`rails g scaffold user last_name:string first_name:sting email:string`

`rails g scaffold reservation user_id:integer date:date beam_target_id:integer`

<!SLIDE small>
# Lösung

    @@@ ruby
    class CreateUsers < ActiveRecord::Migration
      def change
        create_table :users do |t|
          t.string :last_name
          t.string :first_name
          t.string :email

          t.timestamps
        end

        add_index :users, :email, unique: true
      end
    end

<!SLIDE small>
# Lösung
    
    @@@ ruby
    class Reservation < ActiveRecord::Base
      attr_accessible :date, :beam_target_id
      belongs_to :user
      belongs_to :beam_target

      validates_presence_of :user, :beam_target, :date
      validates_uniqueness_of :date, 
        scope: 'beam_target_id',
        message: 'Ist bereits gebucht'
    end
    
    
<!SLIDE small>
# Lösung
`add_index :reservations, [:date, :beam_target_id], :unique => true`

<!SLIDE small>
# Lösung

    @@@ ruby
    class CreateReservations < ActiveRecord::Migration
      def change
        create_table :reservations do |t|
          t.belongs_to :beam_target, null: false
          t.belongs_to :user, null: false
          t.date :date, null: false
          t.timestamps
        end
      end
    end
    
