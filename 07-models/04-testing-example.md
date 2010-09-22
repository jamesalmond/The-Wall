!SLIDE
# Testing a user #
    @@@ ruby
    class User
      validates_format_of :email
      after_create :send_welcome_email
      
      def send_welcome_email
        UserMailer.welcome_mailer(self).deliver
      end
      
    end
!SLIDE bullets incremental
    @@@ ruby
    it "should send an email after create" do
      user = User.new
      UserMailer.should_receive(:welcome_mailer)
        .with(user)
      user.save
    end
* FAIL

!SLIDE bullets incremental
    @@@ ruby
    it "should send an email after create" do
      user = User.new(
        :email => "test@example.com")
      UserMailer.should_receive(:welcome_mailer)
        .with(user)
      user.save
    end
* Pass

!SLIDE bullets incremental
# But I don't want to test the validation! #
* I hear you cry...