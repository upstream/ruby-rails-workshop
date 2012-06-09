!SLIDE
# ActionMailer
Funktioniert wie ein Controller nur das statt HTML Mails versendet werden

!SLIDE
# Mailer erstellen
  * `rails generate mailer NAME`

<!SLIDE small>
# Mail versenden

    @@@ ruby
    def welcome_email(user)
      @user = user
      @url  = "http://example.com/login"
      attachment['file.pdf'] = File.new('path_to/file.pdf')
      mail(:to => user.email, :subject => "Welcome to My Awesome Site")
    end
    
    # Erwartet views/user_mailer/welcome_email.txt.erb

!SLIDE
# Mail view (welcome_email.txt.erb)

    @@@ ruby
    Hallo <%= @user.firstname %>

    come sign in at <%= sign_in_url %>.
  
    <% if @user.age < 20 %>
      Share this on facebook 
    <% end %>

# 

<!SLIDE small>
# Mailer konfigurieren (Bsp für Gmail)

    @@@ ruby
    # in entsprechneder envirment.rb
    config.action_mailer.delivery_method = :smtp
    config.action_mailer.smtp_settings = {
      :address              => "smtp.gmail.com",
      :port                 => 587,
      :domain               => 'upstre.am',
      :user_name            => '<username>',
      :password             => '<password>',
      :authentication       => 'plain',
      :enable_starttls_auto => true  }