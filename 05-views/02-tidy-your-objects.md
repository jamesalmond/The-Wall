!SLIDE
# Don't use internal structure
    @@@ ruby
    # book.rb
    class Book < ActiveRecord::Base
      belongs_to :author
    end
    
    # show.html.haml
    %h2= book.author.name
    
!SLIDE
# Don't use internal structure
    @@@ ruby
    # book.rb
    class Book < ActiveRecord::Base
      belongs_to :author
      def author_name
        author.name
      end
    end

    # show.html.haml
    %h2= book.author_name
!SLIDE
# Don't use internal structure
    @@@ ruby
    # book.rb
    class Book < ActiveRecord::Base
      belongs_to :author
      def author_name
        author.forename + " " + author.surname
      end
    end

    # show.html.haml
    %h2= book.author_name
!SLIDE bullets incremental
# Benefits #
* Promotes creation of public interface
* Easier to swap backend implementations
* Re-use of interface