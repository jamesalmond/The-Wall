!SLIDE bullets incremental
# Service re-use #

* Namespaced controllers
* Within other services
* Integration test set-up

!SLIDE
# Dependency Injection #

    @@@ ruby
    class ReservationCancellationService
    
      def cancel_reservation(repo, res_id)
        res = repo.find_reservation(res_id)
        reservation.cancel!
        # ...
      end
      
    end
!SLIDE
# Dependency Injection #
    @@@ ruby
    # for staff
    ReservationCancellationService
      .cancel_reservation(@hotel, params[:id])
    
    # for admin
    ReservationCancellationService
      .cancel_reservation(Hotel, params[:id])

!SLIDE
# Repository #
    @@@ ruby
    class Hotel
      def self.find_reservation(id)
        # ...
      end
      def find_reservation(id)
       # ...
      end
    end