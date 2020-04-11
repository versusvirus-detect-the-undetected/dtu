# DTU (detect the undetected) - Covid19Clue API message specification 


An application programming interface (API) message specification for covid19 diagnostic data. Enables to re-connect all kinds of disparate third-party covid19 apps safely and securely, to exchange pseudonymous diagnostic profile data as a time-series of messages. Moreover, this API message specification defines also message formats to allow to officially authorize and authenticate a wide range of re-connected covid19 apps as trusted apps. This could be achieved by national and international official public health organizations patronizing a future API and its infrastucture, such as e.g. the Swiss Federal Public Health Office or the U.S. CDC on a national level, and ultimately, the World Health Organization.

Currently, no proper API implementation of Covid19Clue API messages exists (yet), but read on to find some very brief API message end-point scenarios below in section 1, developed during the versusvirus.ch hackathon by our team, see the presentation submitted by the team [here](http://gofile.me/4VWZL/LSdTRdgEC).

The specified Covid19Clue API messages (see below, section 2) are in a JSON-like format, with fields commented and populated with example data, they cannot be used directly in code without modification - they serve for specification purposes only. For their use in large-scale messaging systems, they must be adapted.

## 1 Covid19Clue API message end-point scenario descriptions


### 1.1 Covid19Clue API message end-point scenario for mobile 3rd-party apps 

Re-connect 3rd-party mobile self-diagnose and tracker apps via this endpoint. Provide pseudonymous user diagnosis profile message records for predictions for all 3rd-party public health dashboard apps, epidemiologic dashboards via a messaging API service.

### 1.2 Covid19Clue API message end-point scenario description for health offices, hospitals and physicians 

This API end-point reconnects 3rd-party big-data apps for epidemiologics & prediction in governments as well as 3rd-party health care apps for physicians' patient management to get infection data and patient profiles in near-real time. It e.g. helps physicians to speed up writing and revoking work dispenses in case of positive test results and/or ordered quarantine, hospitalization, etc.

### 1.3 Covid19Clue API message end-point scenario description for test labs, home appliances 

This API end-point scenario connects to Test Lab computers and appliances, as well as home testing IoT (Internet-of-Things) appliances in a machine-to-api scenario.

### 1.4 Covid19Clue API message end-point scenario description for authentication 

This API end-point specification defines app session and token-based authentication message record types. 

### 1.5 Covid19Clue API end-point scenario for authorization 

This API specification defines app and app contact authorization record types. 


## 2. Covid19Clue API JSON-like message record definitions

### 2.1 Profile message record

JSON-like diagnostic profile message record for time series, with (bogus) example data.  
```
"profile-msg": {
    "profile":"369e1fac-820b-4695-98a4-e22901584e0c"                   // pseudonymous diagnostic profile v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string, mandatory
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                     // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string, mandatory
    "user-tx-timestamp":"1586483743"                                   // user transmission GMT time, unix UTC-timestamp, as string, optional 
    "user-tx_tz":"+0100"                                               // user timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string, optional 
    "agent-tx-timestamp":"1586485743"                                  // agent transmission GMT time, unix UTC-timestamp, as string, mandatory
    "agent-tx-tz":"+0100", mandatory                                   // agent timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string
    "agent-gps-lat:"46.9465"                                           // GPS latitude, float value, as string, optional
    "agent-gps-long":"7.4443"                                          // GPS longitude, float value, as string, optional
    "agent-gps-prec":"50"                                              // GPS precision in meters, integer as string, optional
    "age":"55"                                                         // age, integer as string, optional 
    "sex":"m"                                                          // sex, string, "f" = female, "m" = male, optional 
    "infectuous_proximity":"0"                                         // infectuous proximity warning flag, boolean value, default = "0", as string, optional   
    "self-diag-has_fever":"1"                                          // symptom, fever, boolean, as string, optional
    "self-diag-body-temp-scale":"C"                                    // temperature scale, "C" = Celsius, "F" = Fahrenheit, as string, optional
    "self-diag-body-temp":"38.9"                                       // body temperature, float, as string, optional 
    "self-diag-oxy-level:"96"                                          // oxygen level percentage, integer, as string, optional
    "self-diag-cough-sound-AI-result:"74"                              // cough-sound-AI-correspondance percentage, integer, as string, optional
    "self-diag-has-dry-cough":"0"                                      // symptom, dry cough, boolean value, default = "0" as string, optional
    "self-diag-has-freq-sneezing":"0"                                  // symptom, frequent sneezing, boolean value, default = "0"  as string, optional
    "self-diag-has-short-breath:"1"                                    // symptom, short breath, boolean value, default = "0" as string, optional 
    "self-diag-has-breath-difficult:"0"                                // symptom, difficulty breathing, boolean value, as string, optional 
    "self-diag-has-taste-loss":"0"                                     // symptom, taste loss, boolean value, default = "0", as string, optional 
    "self-diag-has-diarrhea":"0"                                       // symptom, diarrhea, boolean value, default = "0" as string
    "self-diag-has-constipation:"0"                                    // symptom, constipation, boolean value, default = "0" as string, optional
    "self-diag-has-stool_color-change:"1"                              // symptom, stool color change, boolean value, default = "0", as string, optional
    "self-diag-has-urine-color-change:"0"                              // symptom, urine color change, boolean value, default = "0", as string, optional  
    "self-diag-has-migraine-like-ache:"1"                              // symptom, migraine-like headache, boolean value, default ="0",  as string optional 
    "self-diag-has-bodyskin-rash":"1"                                  // symptom, sudden body skin rash, boolean value, default ="0", as string, optional
    "self-diag-has-pruritus":"1"                                       // symptom, pruritus (itches), boolean value, default = "0", as string, optional
    "self-diag-has-tachycardy:"1"                                      // symptom, tachycardy at rest, boolean value, default = "0", as string, optional
    "self-diag-has-cardial-arrhythmy:"0"                               // symptom, cardial arrhythmy, boolean value, default = "0", as string, optional 
    "vrfd-diag-has-virustest:"0"                                       // verified tested for virus, boolean value, default = "0", as string, optional 
    "vrfd-diag-virustest-result:"0"                                    // verified virus test result, boolean value, default = "0", as string, optional
    "vrfd-diag-has-immunetest:"0"                                      // verified tested for immunity, boolean value, default = "0", as string, optional 
    "vrfd-diag-immunetest-result:"0"                                   // verified immune test result, boolean value, default = "0", as string, optional
    "vrfd-is-plasma-donor:"0"                                          // verified plasma donor, boolean value, default = "0", as string, optional
    "quarantine":"1"                                                   // "0" = shelter-at-home-commuting,
                                                                       // "1" = shelter-at-home-permanent,  
                                                                       // "2" = ordered-at-home,       
                                                                       // "3" = hospitalized,   
                                                                       // "4" = immunized-released,
                                                                       // integer, as string, optional
}
```
### 2.2 Agent authentication message record 

JSON-like agent authentication message record for time series, with (bogus) example data.    
```
"agent-authn-msg": {                                                   
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string                                              
    "token":"216f00f4be13890449c1852cffd7a8bd9557258eacda56e0b4e8166b943405cc"   // token SHA-256 hash code, as string 
    "session":"e696ebe85bb17ac62ac40e58a07224bb65654935617349ddf538fd5ac176512e" // session SHA-256 hash-code, as string
    "timestamp:"1586485642"                                                      // Authentication GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authentication timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "session-timeout":"3600"                                                     // Authentication timeout, in seconds, as string    
}                                                                                // all fields are mandatory   
```
### 2.3 Contact authentication message record 

JSON-like agent contact authentication message record for time series, with (bogus) example data.    
```
"contact-authn-msg": {                                                   
    "contact":"4e8f2603-4591-4392-952f-bfbe86bd06eb"                             // contact v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "token":"216f00f4be13890449c1852cffd7a8bd9557258eacda56e0b4e8166b943405cc"   // token SHA-256 hash code, as string 
    "session":"e696ebe85bb17ac62ac40e58a07224bb65654935617349ddf538fd5ac176512e" // session SHA-256 hash-code, as string
    "timestamp:"1586485642"                                                      // Authentication GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authentication timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "session-timeout":"3600"                                                     // Authentication timeout, in seconds, as string    
}                                                                                // all fields are mandatory   
```
### 2.3 Agent authorization record

JSON-like agent authorization record, with (bogus) data examples.    
```
"agent-authr": {
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "timestamp:"1586485642"                                                      // Authorization GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authorization time zone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "authorization":"0"                                                          // valid authorization, default = "0" = false, "1" = true
    "type":"user-app"                                                            // Authorization type, "profile-app", "health-app","research-app", "test-lab", "test-site", "self-test-appliance", "nho", "gho", "source", as string
}                                                                                // all fields are mandatory   
```
### 2.4 Contact authorization record 

JSON-like contact authorization record, with (bogus) example data.
```
"contact-authr": {
    "contact":"4e8f2603-4591-4392-952f-bfbe86bd06eb"                                              // agent contact, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
     "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                                                // agent, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
     "timestamp:"1586485642"                                                                       // Authorization GMT time, unix UTC-timestamp, as string 
     "tz":"+0100"                                                                                  // Authorization time zone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
     "agent-name":"Covidtracker"                                                                   // agent name, as string 
     "agent-url":"https://covidtracker.ch"                                                         // valid url, as string 
     "agent-org-fqdn":"covidtracker.ch"                                                           // valid org domain, as string 
     "agent-org-name":"Canton of Bern"                                                            // organization name, as string 
     "agent-org-spoc-usermail":"mailto:admin-at-covidtracker.ch"                                  // valid mail uri, as string
     "agent-org-spoc-password:"2207f568da6b4d1ba8a9cdebb18d5c79847a4fb23a41b27489a3c6d84aeab215"  // sha-256 salted password hash, as string  
     "agent-org-spoc-tel-intl":"41123456789"                                                       // valid international phone number, as string
     "agent-org-spoc-tel-ext":"12345"                                                               // internal extension, as string, optional     
     "agent-org-addr-line-1":"1234, Main Street"                                                   // address line 1, as string                                                                    
     "agent-org addr-line-2":"P.O. Box 1234"                                                       // address line 2, as string, optional 
     "agent-org-city":"Bern"                                                                       // city, as string
     "agent-org-zip":"3000"                                                                        // Postal code, as string     
     "agent-org-region":"BE"                                                                       // region or county code, as string 
     "agent-org-country":"Switzerland"                                                             // Country, as string 
}                                                                                                  // fields are mandatory, exceptions see field comments. 
``` 

