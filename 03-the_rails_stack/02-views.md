!SLIDE
# Views #
!SLIDE
    @@@ ruby
    %h1 Dashboard
!SLIDE
    @@@ ruby
    %h1 Dashboard
    
    if @latest.count > 0
      # show results
    else
      %p No results found!
    end
!SLIDE
    @@@ ruby
    %h1 Dashboard
    
    if @latest.count > 0
      @latest.each do |book|
        %h2= book.author.name
      end
    else
      %p No latest!
    end