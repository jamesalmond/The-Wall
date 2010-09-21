!SLIDE
# Controllers #
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
    end
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
      def update
        @book = Book.find(params[:id])
        @book.update_attributes(params[:book])
      end
    end
    
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
      def update
        @book = Book.find(params[:id])
        if @book.update_attributes(params[:book])
          # redirect
        else
          # render
        end
      end
    end
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
      before_filter :do_something
      def update
        @book = Book.find(params[:id])
        if @book.update_attributes(params[:book])
          # redirect
        else
          # render
        end
      end
    end
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
      before_filter :do_something
      before_filter :load_something
      def update
        @book = Book.find(params[:id])
        if @book.update_attributes(params[:book])
          # redirect
        else
          # render
        end
      end
    end
!SLIDE
    @@@ ruby
    class SomeController < ApplicationController
      before_filter :do_something
      before_filter :load_something
      before_filter :stop_something
      def update
        @book = Book.find(params[:id])
        if @book.update_attributes(params[:book])
          # redirect
        else
          # render
        end
      end
    end