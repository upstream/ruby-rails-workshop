!SLIDE center
# Active Record

!SLIDE
# ActiveRecord::Base
  * Validierungen
  * DB CRUD
  * Abfragen mit Arel
  * Beschreiben von Relationen
  * Zugriff für Massenzuweisungen festlegen (`attr_accessible`)

!SLIDE
#Ruby: Vererbung und Module
    
    @@@ ruby
    class Child < Parent
    end
    
    module MyModule
      class Child
      end
    end
    # => MyModule::Child
      
!SLIDE
# Validierungen
  * Gültigkeitsprüfung beim schreiben in die DB oder bei `.valid?`
  * Bsp
    * validates_presence_of
    * validates_uniqness_of
    * valdiates_format_of
  * weitere hier: http://api.rubyonrails.org/classes/ActiveModel/Validations/HelperMethods.html
  * fehlgeschlagene Validierungen setzen `.errors`

!SLIDE
# Übung
Füge beam_target eine Validierung für density != nil hinzu

!SLIDE
# Lösung
  * validates_presence_of :density

!SLIDE
# Experimente in der Rails Console
  * irb mit Rails
  * `rails console`

# DB CRUD
  `.create(attribute: value)`
  `.find(:id)`
  `.destroy`
  `.all`
  `.update_attributes`
  `.save`
  
# Übung
  Erstelle/Lade/Ändere und Lösche BeamTargets mit `rails console`

!SLIDE
# Abfragemethoden Active Record
  * wichtigsten Abfrage Methoden
    * where
    * select
    * group
    * order
    * limit
    * offset
    * joins
    * includes
    * from
    * having
    * scope

<!SLIDE smaller>
# Scopes

kombinierbare Abfragebedingungen

      @@@ ruby
      class BeamTarget
        scope :small, where("volume < 20")
        scope :light, where("density < 2")
      end

      BeamTarget.small.light # => 
      SELECT `beam_targets`.* FROM `beam_targets` WHERE (density < 2) AND (volume < 20)
  

<!SLIDE>
# Dynamische Finder
  * Methoden die direkt nach Attributen filtern
  * Bsp.
    * `find_by_density(20)`
    * `find_all_by_volume_and_desity(20, 5)`
  
<!SLIDE smaller>
# Ruby: Method missing
wenn eine Methode nicht bekannt ist wir erst `method_missing` aufgerufen bevor ein `NoMethodError` geworfen wird

    @@@ ruby
    class ActiveRecord::Base
      def method_missing(meth, *args, &block)
        if meth.to_s =~ /^find_by_(.+)$/
          run_find_by_method($1, *args, &block)
        else
          super
        end
      end

      def run_find_by_method(attrs, *args, &block)
        attrs = attrs.split('_and_')
        attrs_with_args = [attrs, args].transpose
        where(conditions).all
      end
    end
  
# Übung 

    

