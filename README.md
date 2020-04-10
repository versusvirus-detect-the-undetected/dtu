# Covid19Clue API specification v0.1 - DTU (detect the undetected)

A messaging application programming interface (API) specification for covid19 diagnostic data. Enables to re-connect all kinds of third-party covid19 apps safely to exchange diagnostic data profiles as messages. Moreover, this messaging API specification defines also the messages allowing to officially authorize and authenticate a wide range of re-connected covid19 apps as trusted apps. This can  be achieved by national and international official public health organizations such as e.g. the Swiss Federal Public Health Office or the World Health Organization.

## 1 API usage scenarios description

### 1.1 Covid19Clue API for mobile 3rd-party apps (API end-point scenario)

Re-connect 3rd-party mobile apps to government, doctors, brand them "official".
Provide user symptoms and geo data for predictions for all 3rd-party dashboard apps, epidemiologic dashboards
Consent-based self-diagnostics collection and official geolocator data API service for 3rd-party apps.

### 1.2 Covid19Clue API for health offices, hospitals and physicians (API end-point scenario)

This API reconnects 3rd-party big-data apps for epidemiologics & prediction in governments as well as 3rd party health care apps for physicians' patient management to get infection data and patient profiles in near-real time. It e.g. helps physicians to speed up writing and revoking work dispenses in case of positive test results and/or ordered quarantine, hospitalization, etc.

### 1.3 Covid19Clue API for test labs, home appliances (API end-point scenario)

This API connects Test Lab computers and appliances, as well as home testing Internet-of-Things appliances in the future.
Re-connect 3rd- party mobile apps to government, doctors, brand them "official")

### 1.4 Covid19Clue API authentication (API end-point scenario) 

App session token-based authentication. 

### 1.5 Covid19Clue API authorization (API end-point scenario)

App and app contact authorization. 

## 2. Covid19Clue API JSON data type definitions


### 2.1 Profile message record

Time-series JSON-like diagnostic profile message record, with (bogus) example data.  
```
"profile-msg": {
    "profile":"369e1fac-820b-4695-98a4-e22901584e0c"                   // pseudonymous diagnostic profile v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                     // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "user-tx-timestamp":"1586483743"                                   // user transmission GMT time, unix UTC-timestamp, as string
    "user-tx_tz":"+0100"                                               // user timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "agent-tx-timestamp":"1586485743"                                  // agent transmission GMT time, unix UTC-timestamp, as string
    "agent-tx-tz":"+0100"                                              // agent timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string
    "agent-gps-lat:"46.9465"                                           // GPS latitude, float value as string
    "agent-gps-long":"7.4443"                                          // GPS longitude, float value as string
    "agent-gps-prec":"50"                                              // GPS precision in meters, integer as string
    "age":"55"                                                         // age, int as string
    "sex":"m"                                                          // sex, string, "f" = female, "m" = male 
    "infectuous_proximity":"0"                                         // infectuous proximity warning flag, boolean value, default = "0", as string   
    "self-diag-has_fever": "1"                                         // symptom, fever, boolean, as string
    "self-diag-body-temp-scale":"C"                                    // temperature scale, "C" = Celsius, "F" = Fahrenheit, as string
    "self-diag-body-temp":"38.9"                                       // body temperature, float, as string 
    "self-diag-oxy-level: "96"                                         // oxygen level percentage, integer, as string
    "self-diag-cough-sound-AI-result: "74"                             // cough-sound-AI-correspondance percentage, integer, as string
    "self-diag-has-dry-cough":"0"                                      // symptom, dry cough, boolean value, as string
    "self-diag-has-freq-sneezing":"0"                                  // symptom, frequent sneezing, boolean value, as string
    "self-diag-has-short-breath:"1"                                    // symptom, short breath, boolean value, as string 
    "self-diag-has-breath-difficult:"0"                                // symptom, difficulty breathing, boolean value, as string 
    "self-diag-has-taste-loss":"0"                                     // symptom, taste loss, boolean value, as string
    "self-diag-has-diarrhea":"0"                                       // symptom, diarrhea, boolean value, as string
    "self-diag-has-constipation:"0"                                    // symptom, constipation, boolean value, as string
    "self-diag-has-stool_color-change:"1"                              // symptom, stool color change, boolean value, as string
    "self-diag-has-urine-color-change:"0"                              // symptom, urine color change, boolean value, as string 
    "self-diag-has-migraine-like-ache:"1"                              // symptom, migraine-like headache, boolean value, as string 
    "self-diag-has-bodyskin-rash":"1"                                  // symptom, sudden body skin rash, boolean value, as string
    "self-diag-has-pruritus":"1"                                       // symptom, pruritus (itching), boolean value, default = 0, as string
    "self-diag-has-tachycardy:"1"                                      // symptom, tachycardy at rest, boolean value, default = "0", as string
    "self-diag-has-cardial-arrhythmy:"0"                               // symptom, cardial arrhythmy, boolean value, default = "0", as string 
    "vrfd-diag-has-virustest:"0"                                       // verified tested for virus, boolean value, default = "0", as string 
    "vrfd-diag-virustest-result:"0"                                    // verified virus test result, boolean value, default = "0", as string       
    "vrfd-diag-immunetest-result:"0"                                   // verified immune test result, boolean value, default = "0", as string
     vrfd-is-plasma-donor:"0"                                          // verified plasma donor, boolean value, default = "0", as string
    "stage":"1"                                                        // "0" = undiagnosed,
                                                                       // "1" = self-diagnosed,       
                                                                       // "2" = verified-diagnosed-negative,
                                                                       // "3" = verified-diagnosed-positive,
                                                                       // integer, as string

   "quarantine":"1"                                                    // "0" = shelter-at-home-commuting,
                                                                       // "1" = shelter-at-home-permanent,  
                                                                       // "2" = ordered-at-home,       
                                                                       // "3" = hospitalized,   
                                                                       // "4" = immunized-released,
                                                                       // integer, as string
}
```
### 2.2 Agent authentication message record

Time-series JSON-like agent authentication message record, with (bogus) example data.    
```
"agent-authn-msg": {                                                   
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string                                              
    "token":"216f00f4be13890449c1852cffd7a8bd9557258eacda56e0b4e8166b943405cc"   // token SHA-256 hash code, as string 
    "session":"e696ebe85bb17ac62ac40e58a07224bb65654935617349ddf538fd5ac176512e" // session SHA-256 hash-code, as string
    "timestamp:"1586485642"                                                      // Authentication GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authentication timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "session-timeout":"3600"                                                     // Authentication timeout, in seconds, as string    
}
```
### 2.3 Contact authentication message record

Time-series JSON-like agent contact authentication message record, with (bogus) example data.    
```
"contact-authn-msg": {                                                   
    "contact":"4e8f2603-4591-4392-952f-bfbe86bd06eb"                             // contact v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "token":"216f00f4be13890449c1852cffd7a8bd9557258eacda56e0b4e8166b943405cc"   // token SHA-256 hash code, as string 
    "session":"e696ebe85bb17ac62ac40e58a07224bb65654935617349ddf538fd5ac176512e" // session SHA-256 hash-code, as string
    "timestamp:"1586485642"                                                      // Authentication GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authentication timezone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "session-timeout":"3600"                                                     // Authentication timeout, in seconds, as string    
}
```
### 2.3 Agent authorization record

JSON-like agent authorization dataset, with (bogus) data examples.    
```
"agent-authr": {
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                               // agent v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "timestamp:"1586485642"                                                      // Authorization GMT time, unix UTC-timestamp, as string 
    "tz":"+0100"                                                                 // Authorization time zone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
    "authorization":"0"                                                          // valid authorization, default = "0" = false, "1" = true
    "type":"user-app"                                                            // Authorization type, "profile-app", "health-app","research-app", "test-lab", "test-site", "self-test-appliance", "nho", "gho", "source", as string
}
```
### 2.4 Contact authorization record 
JSON-like contact authorization dataset, with (bogus) example data.
```
"contact-authr": {
    "contact": "4e8f2603-4591-4392-952f-bfbe86bd06eb"                                              // agent contact, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
     "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                                                // agent, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
     "timestamp:"1586485642"                                                                       // Authorization GMT time, unix UTC-timestamp, as string 
     "tz":"+0100"                                                                                  // Authorization time zone, string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string 
     "agent-name":"Covidtracker"                                                                   // agent name, as string 
     "agent-url":"https://covidtracker.ch"                                                         // valid url, as string 
     "agent-org-fqdn": "covidtracker.ch"                                                           // valid org domain, as string 
     "agent-org-name": "Canton of Bern"                                                            // organization name, as string 
     "agent-org-spoc-usermail": "mailto:admin-at-covidtracker.ch"                                  // valid mail uri, as string
     "agent-org-spoc-password: "2207f568da6b4d1ba8a9cdebb18d5c79847a4fb23a41b27489a3c6d84aeab215"  // sha-256 salted password hash, as string  
     "agent-org-spoc-tel-intl":"41123456789"                                                       // valid international phone number, as string
     "agent-org-spoc-tel-ext:"12345"                                                               // internal extension, as string     
     "agent-org-addr-line-1: "1234, Main Street"                                                   // address line 1, as string                                                                    
     "agent-org addr-line-2: "P.O. Box 1234"                                                       // address line 2, as string 
     "agent-org-city: "Bern"                                                                       // city, as string
     "agent-org-zip: "3000"                                                                        // Postal code, as string     
     "agent-org-region":"BE"                                                                       // region or county code, as string 
     "agent-org-country":"Switzerland"                                                             // Country, as string 
}
``` 

