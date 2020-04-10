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

Main dataset definition for messaging system time series. All personal diag data is optional, UUID for user, agent is mandatory.  
```
"diag-data": {
    "user":"369e1fac-820b-4695-98a4-e22901584e0c"                      // v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                     // v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "tx-timestamp":"                                                   // transmission time, unix UTC-timestamp, as string
    "tx-tz":"GMT+2"                                                    // transmission timezone UTC time offset code, as string 
    "age":"55"                                                         // age, int as string
    "sex":"m"                                                          // sex, string, "f" = female, "m" = male 
    "gps-lat:"46.9465"                                                 // GPS latitude, float value as string
    "gps-long":"7.4443"                                                // GPS longitude, float value as string
    "gps-prec":"50"                                                    // GPS precision in meters, integer as string                  
    "self-diag-has_fever": "1"                                         // boolean, as string
    "self-diag-temp-scale":"C"                                         // "C" = Celsius, "F" = Fahrenheit, as string  
    "self-diag-fever-temp":"38.9"                                      // float, as string 
    "self-diag-has-dry-cough":"0"                                      // boolean value, as string 
    "self-diag-has-taste-loss":"0"                                     // boolean value, as string 
    "vrfd-diag-has-test-positive:"0"                                   // boolean value, as string       
    "vrfd-test-positive-by":"6620a86f-e87c-4566-9a45-b8ea32a2885d"     // testing agent's UUID, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4, as string
    "vrfd-has-test-immunized:"0"                                       // boolean value, as string  
    "vrfd-test-positive-by":"8dbee094-90d7-4faa-9e5f-fdad0ed4a7a3"     // string, testing agent-UUID, v4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4
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
    "alert_message":"You tested covid19 negative."      // alert message, as string
    "alert_UTC_timestamp":"1586485642"                  // unix UTC timestamp, as string
    "alert_tz":"+0200"                                  // +/-"hhmm", including daylight saving time, as string  
    "alert_locale":"de_ch"                              // unix locale,  as string
    "alert_type":"1"                                    // type, 1 - user message, 2 - system message, integer as string
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
