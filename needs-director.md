# Visit-counter for a Director

Scenario: Show patient visits during working days and holidays

  Given A patient gets a new entry card from entry card issuer on admission to hospital
  When A patient gets a new entry card on working day
  Then increment the patientCountOnWorkingDay by one 
  
  Given The patient submits the entry card to the entry card issuer once the patient is discharged from the hospital
  When A patient submits the entry card on a working day
  Then decrement the patientCountOnWorkingDay by one
  
  Given A patient gets a new entry card from entry card issuer on admission to hospital
  When A patient gets a new entry card on a holiday
  Then increment the patientCountOnHoliday by one 
  
  Given The patient submits the entry card to the entry card issuer once the patient is discharged from the hospital
  When A patient submits the entry card on a holiday
  Then decrement the patientCountOnHoliday by one

Scenario: Compute parking slots to reserve for visiting specialists

  Given
  When
  Then
