!SLIDE
# Controller

!SLIDE
# ApplicationController
Basis Controller der Allgemeine RoutingRegeln umsetzt und .

* Authentifizierung
* Parameter Filter
* CSRF Schutz (`protect_from_forgery`)

<!SLIDE bullets>
# Filter

werden 

   * vor (`before_filter`)
   * nach (`after_filter`) 
   * oder um (`arround`)

einer Action ausgeführt. ein `false` Wert beendet den Request vorzeitig.

!SLIDE
# Response Formate
  * Resourcen können verschiedene Representationsformate haben
  * diese werden über die selbe Action bedient
  * `respond_to do |format|`
  
<!SLIDE small>
# Response Formate BSP  
    @@@ ruby
    respond_to do |format|
      format.html # show.html.erb
      format.json { render json: @beam_target }
    end

.notes erläutern was in render passiert  
