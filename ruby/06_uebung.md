!SLIDE
# Übung
Definiere eine Klasse `BeamTarget` dessen Instanzen mit einer Dichte (gramm/qcm) initialisiert werden und optional einem Volumen(qcm), Standardvolumen ist 20 qcm. Für jedes BeamTarget soll sich die Masse mit Einheit (gramm) als String ausgeben lassen. Auf die gesetzen Attribute soll nur lesend zugegriffen werden können.

!SLIDE
# Lösung
    @@@ ruby
    class BeamTarget
      attr_reader :density, :volume
      def initialize(density, volume = 20)
        @density = density
        @volume = volume
      end
      
      def mass
        (@density * @volume).to_s + ' gramm'
      end
    end
  