!SLIDE
# capistano
Framework das es erlaubt Tasks auf mehreren Systemen gleichzeitig auszuführen.

.notes funktioniert wie rake

!SLIDE
# capistano vorraussetzungen
 * zugangn uber SSH
 * Gleiches Passwort oder public key auf allen Servern

.notes supports tunneling over gateways for VPN and Firewall


!SLIDE
# struktur
  * `Capfile` im Projekt Verzeichnis
  * `deploy.rb` in config
  * env spezifische config in `config/deploy/[env].rb`
  * cap Skript um Tasks auszuführen
  * capify Skript um capistrano zu initialisieren.

!SLIDE
# Funktionen
  * Zugriff über ssh auf remote Servern
  * verteilen der sourcen via SCP und/oder GIT/SVN...
  * vorhalten meherer Versionen und Rollbacks
  * Maintainence mode 
  * rollenspezifische Task für Server
  * Mehrere Enviroments (über Erweiterung)

!SLIDE
# Beste Practice: Deployment Enviroments
  * Development: Lokaler Rechner
    * 
  * Staging: Server der dem Live System ähnlich ist
    * hier finded finale QA statt
  * Production: Live Server
    * hier wird kein Code 'schnell' gefixed

<!SLIDE smaller>
# Standard Config
  
    @@@ruby
    set :application, "beam_targets"
    set :repository,  "set your repository location here"

    set :scm, :subversion
    # Or: `accurev`, `bzr`, `cvs`, `darcs`, `git`, `mercurial`, `perforce`, `subversion` or `none`

    role :web, "your web-server here"   # Your HTTP server, Apache/etc
    role :app, "your app-server here"   # This may be the same as your `Web` server
    # This is where Rails migrations will run
    role :db,  "your primary db-server here", :primary => true 
    role :db,  "your slave db-server here"

    namespace :deploy do
      task :start do ; end
      task :stop do ; end
      task :restart, :roles => :app, :except => { :no_release => true } do
        run "#{try_sudo} touch #{File.join(current_path,'tmp','restart.txt')}"
      end
    end
    
.notes show adv config