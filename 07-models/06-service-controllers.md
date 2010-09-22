!SLIDE 
# Service Controllers
    @@@ ruby
    # users_controller.rb
    class UsersController < ApplicationController
      def create
        @user = User.new(params[:user])
        if @user.save
          redirect_to dashboard_path
        else
          render :new
        end
      end
    end

!SLIDE
# Service Controllers #
    @@@ ruby
    # users_controller.rb
    class UsersController < ApplicationController
      def create
        UserService.create_user(params[:user])
        redirect_to dashboard_path
      end
    end
!SLIDE
# User Service #
    @@@ ruby
    class UserCreationService
      def self.create_user(attributes)
        user = User.new(attributes)
        raise UserCreationError unless user.save
        SignupNotificationService.new_user(user)
        # ....
      end
    end
!SLIDE
# Service Controllers #
    @@@ ruby
    # users_controller.rb
    class UsersController < ApplicationController
      def create
        UserService.create_user(params[:user])
        redirect_to dashboard_path
      rescue UserCreationError => error
        render :new
      end
    end
!SLIDE
# What if we can't send the introduction email? #
!SLIDE
    @@@ ruby
    # users_controller.rb
    class UsersController < ApplicationController
    
      def create
        UserService.create_user(params[:user])
        redirect_to dashboard_path
      rescue UserCreationError => error
        render :new
      rescue EmailSendingError => error
        flash[:warning] = 
          "We couldn't send your intro email..."
        redirect_to dashboard_path
      end
      
    end
!SLIDE bullets incremental
# Note: #
* The controller doesn't know about the persistence layer
* We describe the 'normal' path through the system
* We have more than a boolean choice for errors
* We can now handle errors differently