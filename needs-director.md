# Visit-counter for a Director

Scenario: Show patient visits during working days and holidays

  Given A patient gets a new entry card from entry card issuer on admission to hospital
  When A patient gets a new entry card on working day
  Then increment the "patient counter on working day" by one
  
  Given The patient submits the entry card on discharge from the hospital
  When A patient submits the entry card on a working day
  Then decrement the "patient counter on working day" by one
  
  Given A patient gets a new entry card from entry card issuer on admission to hospital
  When A patient gets a new entry card on a holiday
  Then increment the "patient counter on holiday" by one
  
  Given The patient submits the entry card on discharge from the hospital
  When A patient submits the entry card on a holiday
  Then decrement the "patient counter on holiday" by one

Scenario: Compute parking slots to reserve for visiting specialists

  Given A visiting specialist confirms the visit
  one hour before the visit
  And the director reserves a parking spot one hour in advance
  When A visiting specialist confirms the visit
  Then increment the "reserve parking for specialist counter" by one

  Given A visiting specialist confirms the visit
  one hour before the visit
  And the director reserves a parking spot one hour in advance
  When A visiting specialist cancels the visit
  Then decrement the "reserve parking for specialist counter" by one

  Given A visiting specialist confirmed the visit
  When The visiting specialist gets entry card
  Then decrement the "reserve parking for specialist counter" by one
  And increment the "specialist parking in use counter" by one

  Given A visiting specialist confirmed the visit
  When The visiting specialist submits the entry card
  Then decrement the "specialist parking in use counter" by one
