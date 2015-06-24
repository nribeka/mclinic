# Workflow #

  * prefetch the patient demographic information only. this way we only downloading data the user will first see. user wont open every patient data (so, we're effectively reducing the cost of downloading unused data, reducing the time of the download and conserving the life of the battery).
  * every time a user open a patient, the download will start (should be fast enough to transfer small chunk of data from the server, gzip the data)

  * I.e. treat it like an email client. Allow work from offline for those not connected.

  * Should ideally save the last synchronization time to allow for the delta to be downloaded (IMEI / last sych time). Ideally saved on server.

  * with this in mind, if we have a cohort of 100 patients with 2 obs and 2 preferred form for each patient, with the current approach we will download 100 patients, 200 obs and 200 preferred form information. with the chunked approach, we only download 100 patients and download 2 obs and 2 preferred form on demand.
  * this assuming the chw always have connectivity
  * we can also have the option to download the entire thing as well (the sync button will do this, but by default it should only download the patient data and then dynamically fetch the obs and preferred form information)
  * the default behavior is assuming 3g connection. we will have option for work offline which will trigger downloading all needed information. kinda similar to the email client. you prefetch the header of the email, and when you click the email it will download the content. and then when the user select the work offline options, the system will download all emails for offline reading.