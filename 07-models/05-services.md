!SLIDE bullets incremental
# Service Objects #
* to the rescue!

!SLIDE bullets incremental
# They contain the business logic #

!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        user.save
      end
    end
!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        user.save
        UserMailer.welcome_mailer(user).deliver
      end
    end
!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        user.save
        UserMailer.welcome_mailer(user).deliver
        AdminMailer.new_user(user).deliver
      end
    end
!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        user.save
        SignupNotificationService.new_user(user)
      end
    end
!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        user.save
        SignupNotificationService.new_user(user)
        # ....
      end
    end
!SLIDE bullets incremental
# Benefits #
* Extract logic from the persistence layer
* Testable outside the controller
* Re-usable throughout application and tests
* Well suited to refactoring
* Intent is now explicit (i.e. email sending)
* They don't have to touch the database!