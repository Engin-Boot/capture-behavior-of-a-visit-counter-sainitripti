# Visit-counter technical needs

Scenario: Recover across restarts of the server
that runs the visit-counter

  Given Server stores backup of data for visit-counter in cloud every hour
  When Server restarts
  Then Server retrieves last checkpoint from cloud
  And updates values of visit-counter data

Scenario: Reconcile counts if the sensor is offline for a while

  Given Time duration for which sensor is offline
  When sensor comes online
  Then determine average increment or decrement in values
  using machine learning algorithms and data trends
  And increment data values by estimated values
