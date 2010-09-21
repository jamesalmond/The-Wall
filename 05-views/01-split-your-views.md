!SLIDE
# Views #

!SLIDE

# Split them up
    @@@ ruby
    # some_controller.rb
    def show
      @latest = Model.latest
    end
    
    # show.html.haml
    if @latest.count > 0
      # show results
    else
      %p No results found!
    end

!SLIDE
# Split them up
    @@@ ruby
    # some_controller.rb
    def show
      @latest = Model.latest
      if @latest.count > 0
        render :show
      else
        render :no_results
      end
    end

    # show.html.haml
    # show results
    
    # no_results.html.haml
    %p No results found!
    
!SLIDE
# Split them up
    @@@ ruby
    # some_controller.rb
    def show
      @latest = Model.latest
      if @latest.count > 0
        render :show
      else
        render :no_results, :status => :404
      end
    end

!SLIDE bullets incremental
# Benefits #
* Removes logic from view
* Makes views more readable
* Leaves the decision of what to render to the Controller