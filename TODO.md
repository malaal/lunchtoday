# TODO

## DO NOW
  - JSON Changes:
    - Add host port (to change 8080)
    - Add DEBUG switch
    - Add email send throttling
    - Add a separate "from" address in the SMTP section separate from SMTP username
    - Add the admin user/pass
  - Can cherrypy monitor the JSON and restart on saved changes?

  - Change the DB and Monitor so that it can resume a running event if the program is terminated

  - Add a button on the email to have an "I'm not coming" option
    - Include the list of people coming and not coming in the end-of-event email
    - Allow users to say "I'm not coming" and thereby cancel their previous vote

  - Improve the Results page:
    - Include the schultze outputs on the results page
  - Put a reminder link to the results page on the "vote received" page, and on the end-event email
  
  - Set a minimum rank threshold below which restaurants are retired from the list
    - This won't work since ranks are 0-5
    - Perhaps: Enforce a time window or number of votes beyond which a restaurant is removed with a below-threshold rank

## DO LATER  
  - If a user goes back to change their vote, populate the screen with their old vote
  - Beautify the CSS for the emails, etc
  - Clean up the admin page
  - Option to hide votes until after the event has closed (to prevent bias)

  - Verify:
    - The ranking algorithm
    - A good selection of restaurant choices in the getChoices algorithm
  - Add an "admin" or "role" column to users so future users can have admin rights granted

## FUTURE IDEAS
  - Separate out the db-based HTML generation from the cherryPy front end so it can be swapped out (and is cleaner)
  - Improve the SQLAlchemy to be more relationship and less query based?
    - ex: use event = relationship("Event") and event_id=ForeignKey("Event")

  - Allow operator to change the number of restaurants that appear in a vote
  - Allow users to "log in" and view their:
    - voting history
    - personal restaurant ranking (vs the global ranking)
  - Allow users to "auto-vote" based on their existing personal ranking
  - Track rank history and plot how restaurants change over time
    - Store entore rank history in the DB or recalculate to show this data? 
    - Should be easily recalculable by only calculating votes up to a certain date
  
  - Page to allow an admin to start a manual event at will, with a fixed list of restaurants
    - Allow this to override the automatic event
    - Or allow admin to manually set up the next automatic event early
  - Add a button to manually end (or cancel) an event
  
  - When a user is removed from the list, what happens to their votes?
    - Stay in place so rankings are continuous
    - Deleted with rankings immediately recalculated
  
  - Restaurant Management:
    - Restaurants need to be effectively removed (such as if they close) without ruining all the DB relationships.
    - Allow admin to modify the name and visit date of a restaurant
  - Improve the ranking algorithm:
    - Ensure the algorithm actually holds up after a few weeks!
    - Add a cooldown so restaurants fade in ranking (and are then more likely to be selected for a new vote)
  - Use a nonce instead of an email address to authenticate users to prevent voter fraud
    - Send the nonce in the email to each user

  - Make the lunch emails a macro-based string that operators can edit outside of the code

  - Allow for multiple parallel lunch groups
    - Multiple user lists
      - Allow users to opt-in to groups by choice
      - Allow admins to moderate lists
    - Customizable event schedules
    - Group and Global admin rights
    - Custom or global restaurant lists with their own visit dates
      - Allow the group to share the global ranking or generate their own    

## BUGS
  - Doesn't work if there are fewer than five restaurants on the list
    - Instruct user to add some before letting Manager start a vote session
  - Stop the loop if errors happen sending emails?    

-----------------------------------------------------------------------
# NOTES

