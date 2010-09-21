!SLIDE
# Use Presenters #
    @@@ ruby
    # dasboard_controller.rb
    def show
      @latest = Model.latest
      @greatest = Model.greatest
      @calendar = Events.all(:date => Date.today)
    end
    # dashboard.html.haml
    %ul
      @latest.each do # ....
    %ul
      @greatest.each do # ....
    %ul
      @calendar.each do # ....
      
!SLIDE
# Use Presenters #
    @@@ ruby
    # dasboard_controller.rb
    def show
      @dasboard = DashboardPresenter.new
    end
    # dashboard.html.haml
    %ul
      @dashboard.latest.each do # ....
    %ul
      @dashboard.greatest.each do # ....
    %ul
      @dashboard.calendar.each do # ....
!SLIDE
# Use Presenters #
    @@@ ruby
    class DashboardPresenter
      def latest
        Model.latest
      end
      def greatest
        Model.greatest
      end
      def calendar
        CalendarPresenter.new(:date => Date.today)
      end
    end

!SLIDE bullets incremental
# Benefits #
* Reduces the size of controller
* Reduces the number of instance variables to keep track of
* Presenters testable outside of the view