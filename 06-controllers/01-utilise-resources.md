!SLIDE
# Utilise Resources #
    @@@ ruby
    # routes.rb
    resources :books do
      member do 
        get 'status'
        put 'update_status'
      end
    end
    # books_controller.rb
    class BooksController < ApplicationController
      def index # show, create, update, destroy
      end
      def status
      end
      def update_status
      end
      # .....
!SLIDE
# Utilise Resources #
    @@@ ruby
    # routes.rb
    resources :books do
      resource :status, 
        :controller => :book_status
    end
    
    # book_status_controller.rb
    class BookStatusController < ApplicationController
      def show
      end
      def update
        @book.set_status(params[:status])
      end
    end

!SLIDE bullets incremental
# Benefits #
* Nice URLs (/books/1/status, /books/1/status/edit)
* Smaller controllers
* Standard methods (show, create)
* Easier to find functionality