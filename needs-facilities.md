# Visit-counter for a Facilities Manager

Scenario: Report visitor trends during a week of operation

  Given "entry card issuer" issues entry card to each category of visitors
  (patients, people related to patients, visiting specialists, others)
  And different modules keeps a count of patients,
  people related to patients, visiting specialists and others
  visiting the hospital in a day using data from "entry card issuer"
  and updates the corresponding tables
  in the "visit counter" database at the end of the day
  
  When director clicks "View trends during the week"
  
  Then display a report of
  total visitors on each day of the week,
  average visitors in the week,
  day with largest number of visitors
  and day with smallest number of visitors
  for each category of visitors
  using one week record from corresponding tables in database

Scenario: Alert when seating capacity is full

  Given Data from footfall sensor is available
  And a module keeps count of total people inside the hospital in real time

  When count by module exceeds total seating capacity (fixed value)

  Then module raises alert "Seating capacity is full"
