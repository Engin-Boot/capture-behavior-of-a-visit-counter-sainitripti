# Visit-counter for a Facilities Manager

Scenario: Report visitor trends during a week of operation

  Given Total footfall on each day of the week
  And total entry cards issued to patients each day of the week
  And total entry cards issued to visiting specialist each day of the week
  And total attendance of staff each day of the week
  And button to generate reports for the week
  
  When I click "View trends during the week" button
  
  Then I see
  Bar chart for footfall in the week
  And bar chart for new patients in the week
  And bar chart for daily visiting specialists in the week
  And bar chart for daily staff attendance in the week
  (one bar represents one day of the week)
  And table for average of footfall,
  average of new patients,
  average of visits by visiting staff
  and average of staff attendance for the week
  (average "equals" sum of values for all days of the week
  "divides" total number of days)
  And table for largest and smallest values of footfall,
  largest and smallest values of new patients,
  largest and smallest values of visits by visiting staff
  and largest and smallest values of staff attendance for the week

Scenario: Alert when seating capacity is full

  Given Data from footfall sensor is available
  When incoming footfall in a day "minus" outgoing footfall in a day
  is greater than total seating capacity
  Then raise alert "Seating capacity is full"
