!SLIDE
# ActionMailer
Funktioniert wie ein Controller nur das statt HTML Mails versendet werden

!SLIDE
# Mailer erstellen
  * `rails generate mailer NAME`

!SLIDE
# Mail versenden

    @@@ ruby
    def welcome_email(user)
      @user = user
      @url  = "http://example.com/login"
      attachment['filename']
      mail(:to => user.email, :subject => "Welcome to My Awesome Site")
    end
    
    # Erwartet views/user_mailer/welcome_email.txt.erb

!SLIDE
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