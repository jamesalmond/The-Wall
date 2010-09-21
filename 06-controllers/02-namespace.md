!SLIDE
# Namespace #
    @@@ ruby
    #routes.rb
    resources :users
    
    #users_controller.rb
    class UsersController < ApplicationController
      def index
        if @user.admin?
          @users = User.all
        else
          @users = @user.group_users
        end
      end
    end
!SLIDE
# Namespace #
    @@@ ruby
    #routes.rb
    namespace :admin do
      resources :users
    end
    namespace :staff do
      resources :users
    end
!SLIDE
# Namespace #
    @@@ ruby
    #admin/users_controller.rb
    class Admin::UsersController < Admin::ApplicationController
      def index
        @users = User.all
      end
    end
    
    #staff/users_controller.rb
    class Staff::UsersController < Staff::ApplicationController
      def index
        @users = @user.group_users
      end
    end
!SLIDE bullets incremental
# Benefits #
* Deal with one role at a time
* Clearly segregate views
* Removes unnecessary logic