!SLIDE
# Models #

!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
    end
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :field
    end
        
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :field
      has_many :others
    end
    
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :input
      has_many :other_objects
      # save, create, build
    end
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :input
      has_many :other_objects
      # save, create, build
      # find, first, all
    end
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :input
      has_many :other_objects
      # save, create, build
      # find, first, all
      after_create :send_email
    end
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :input
      has_many :other_objects
      # save, create, build
      # find, first, all
      after_create :send_email
      
      def process_new_task
        # logic...
      end
    end
!SLIDE
    @@@ ruby
    class Model < ActiveRecord::Base
      validates_presence_of :input
      has_many :other_objects
      # save, create, build
      # find, first, all
      after_create :send_email

      def process_new_task
        # logic...
      end
      # "parent objects"
    end