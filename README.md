# Covid19Clue API - DTU (detect the undetected)

(work in progress)
A web-based application programming interface to re-connect all third-party apps safely to exchange real-time diagnostic ​
data, allowing to officially "brand" them as trusted apps by the Swiss Federal Office for Public Health or the WHO. ​

## 1 API usage scenarios and basic use cases description

### 1.1. Covid19Clue API for mobile 3rd-party apps (API end-point scenario)
Re-connect 3rd-party mobile apps to government, doctors, brand them "official".
Provide user symptoms and geo data for predictions for all 3rd-party dashboard apps, epidemiologic dashboards
Consent-based self-diagnostics collection and official geolocator data API service for 3rd-party apps.

### 1.2. Covid19Clue API for officials (BAG, doctors) (API end-point scenario)
This API reconnects 3rd-party big-data apps for epidemiologics & prediction in governments as well as 3rd party health care apps for physicians' patient management to get infection data in near-real time. It also helps doctors to speed up work dispenses in case of positive test results, and respective quarantining


### 1.3 Covid19Clue API for test labs, home appliances (API end-point scenario)

This API connects Test Lab computers and appliances, as well as home testing Internet-of-Things appliances in the future.
Re-connect 3rd- party mobile apps to government, doctors, brand them "official")

### 1.4 Covid19Clue API authentication (API end-point scenario) 

App/Session token-based authentication (tbd) 

### 1.5 Covid19Clue API Geolocator (API back-end scenario)

This API verifies and/or creates trusted geolocations from user self-diagnostic time-series data from 3rd-party apps.

## 2. Covid19Clue API JSON data type definition

### 2.1 diag-data

Time-series dataset definition for messaging system. All data is optional, except UUIDs for the user and the agent, is mandatory.  
```
"diag-data": {
    "user":"369e1fac-820b-4695-98a4-e22901584e0c"                      // v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                     // v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "tx-timestamp":"                                                   // transmission time, unix UTC-timestamp, as string
    "tx_tz":"+0100"                                                    // string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string  
    "age":"55"                                                         // age, int as string
    "sex":"m"                                                          // sex, string, "f" = female, "m" = male 
    "gps-lat:"46.9465"                                                 // GPS latitude, float value as string
    "gps-long":"7.4443"                                                // GPS longitude, float value as string
    "gps-prec":"50"                                                    // GPS precision in meters, integer as string                  
    "self-diag-has_fever": "1"                                         // symptom, fever, boolean, as string
    "self-diag-body-temp-scale":"C"                                    // temperature scale, "C" = Celsius, "F" = Fahrenheit, as string
    "self-diag-body-temp":"38.9"                                       // body temperature, float, as string 
    "self-diag-oxy-level: "96"                                         // oxygen level percentage, integer, as string
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
    "self-diag-has-pruritus":"1"                                       // symptom, pruritus (itching), boolean value, as string
    "self-diag-has-tachycardy:"1"                                      // symptom, tachycardy at rest, boolean value, as string
    "self-diag-has-cardial-arrhythmy:"0"                               // symptom, cardial arrhythmy, boolean value, as string 
    "vrfd-diag-virustest-result:"0"                                    // verfied virus test result, "0" = negative, "1" = positive, boolean value, as string       
    "vrfd-diag-immunetest-result:"0"                                   // verfied immune test result, "0" = negative, "1" = positive, boolean value, as string       
}
```
### 2.2 auth-data
```
"auth-data": {
    "auth-token":"216f00f4be13890449c1852cffd7a8bd9557258eacda56e0b4e8166b943405cc"   // SHA-256 hash code, as string                                                    
    "authorize-agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                          // v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string                                              
    "auth-timeout":"3600"                                                             // seconds, as string    
    }
}
```
### 2.3 alert-data 
```
"alert-data": {
    "alert-rcpt":"369e1fac-820b-4695-98a4-e22901584e0c" // user UUID, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "alert-message":"You tested covid19 negative."      // alert message, as string
    "alert-timestamp":"1586485642"                      // unix UTC timestamp, as string
    "alert-tz":"+0100"                                  // string concatenation of "+" or "-" with "hhmm" time format, excluding daylight saving time, as string  
    "alert-locale":"de_ch"                              // unix locale,  as string
    "alert-type":"1"                                    // type, 1 - user message, 2 - system message, integer as string
}
```
## API function calls
```

```
### get_latest_user_data(api-auth-data, GUID)
```

```
### get_user_ts_data(api_auth_data,GUID);
```

```
### get_users(api-auth-data, pagination as integer);
```

```
### get_user_dataset_list(api-auth-data, pagination as integer);
```

```
### push_user_alert(api-auth-data, GUID);
```

```
### create_user(api_auth_data)
```

```
(/work in progress)
