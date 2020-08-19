# Visit-counter for a Director

Scenario: Show patient visits during working days and holidays

  Given "entry card issuer" issues entry card to patients
  on admission to the hospital
  And "patient visit tracker" module keeps a count of patients
  visiting the hospital in a day using data from "entry card issuer"
  and updates the "patient visit" table
  in the "visit counter" database at the end of the day
  
  When director clicks "Show patient visits"
  
  Then display a report of
  average patient visits on each days of the week (both working days and holidays),
  working day with largest number of patient visits,
  working day with smallest number of patient visits,
  holiday with largest number of patient visits
  and holiday with smallest number of patient visits
  using last fifty records from "patient visit" table in database
  
Scenario: Compute parking slots to reserve for visiting specialists

  Given A schedule for all visiting specialists is available
  And director has configured system timer to trigger in every six hours

  When system timer triggers

  Then calculate count of "visiting specialists"
  visiting the hospital in the next six hours and store the result in
  "visiting specialist parking" table in the "visit counter" database with timestamps
