# Visit-counter technical needs

Scenario: Recover across restarts of the server
that runs the visit-counter

  Given Server stores backup of data for visit-counter in cloud every hour
  When Server restarts
  Then Server retrieves last checkpoint from cloud
  And updates values of visit-counter data

Scenario: Reconcile counts if the sensor is offline for a while

  Given sensor is offline
  And server stores sensor data in the cloud every five minutes
  When sensor comes online
  Then Server retrieves last checkpoint of sensor data from cloud
  And reset the sensor with the retrieved data
  And add log with the time stamps
