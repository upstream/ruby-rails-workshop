!SLIDE center
# Views

!SLIDE
# Views im Controller bestimmen
  * default render
  * render 'viewname'
  * render 'other_controller/viewname'
  * render inline: '<html><body>Hello World</body></html>'
  * redirect_to
  * head

!SLIDE  
# Layouts
  Werden bei jeder View 'drumherum' gerendert, Standard ist in `layout/application.html.erb`. 
  
  Die View wird an die stelle des von `yield` geschrieben.
  
    @@@ html
    <html>
      <body>
      <%= yield %>
      </body>
    </html>

!SLIDE  
# Ruby: yield
  yield ruft den übergeben block auf and der stelle im Code wo yield steht.

!SLIDE
# Layout im Controller setzen
    @@@ ruby
    class MyController  
      layout 'name'
      
      def foo
        render layout: 'bar'
      end
    end
    
.note Layout wird vererbt

!SLIDE
# ViewHelper

Hilfsmethoden die View-Logik kapseln. Werden in `helpers/model_name_helpers.rb` abgelegt

!SLIDE
# Rails ViewHelpder
  * image_tag
  * form_tag
  * stylesheet_link_tag
  * javascript_include_tag
  * link_to

!SLIDE smaller
# URL Helper
Methoden die auf Grundlage der Routen urls zurückgeben

  * signular_path(id) - show
  * signular_path POST- create
  * new_singular_path - new
  * edit_singular_path(id) - update
  * signular_path(id) DELETE - destroy
  * plural_path - index

`rake routes` zeigt die Routen der App
  
    
