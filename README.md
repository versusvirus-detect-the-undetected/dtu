# dtu - detect the undetected - Covid19Clue API (work in progress)
A web-based application programming interface to re-connect all third-party apps safely to exchange real-time diagnostic ​
data, allowing to officially "brand" them as trusted appsby the Swiss Federal Office for Public Health or the WHO. ​

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

## 2. API JSON data type definition (time series)   
```
diag-data {
    "user":"369e1fac-820b-4695-98a4-e22901584e0c"                      // string 4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4
    "agent":"d303aea7-3604-46c5-84c9-ad2758fb2852"                      // string 4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4
    "tx-timestamp":"                                                   // UTC-timestamp
    "age":"55"                                                         // int as string
    "sex":"m"                                                          // string, "f" = female, "m" = male, 
    "gps-lat:"46.9465"                                                 // float value as string
    "gps-long":"7.4443"                                                // float value as string
    "gps-prec":"50"                                                    // integer as string, meters                  
    "self-diag-has_fever": "1"                                         // boolean as string
    "self-diag-temp-scale":"C"                                         // string, "C" = Celsius, "F" = Fahrenheit  
    "self-diag-fever-temp":"38.9"                                      // float as string 
    "self-diag-has_dry-cough":"0"                                      // boolean as string 
    "self-diag-has_taste-loss":"0"                                     // boolean as string 
    "vrfd-diag-has_test-positive:"0"                                   // boolean as string       
    "vrfd-test-positive-by":"6620a86f-e87c-4566-9a45-b8ea32a2885d"     // string, testing agent-UUID string 4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4
    "vrfd-has-test_immunized:"0"                                       // boolean as string  
    "vrfd-test-positive-by":"8dbee094-90d7-4faa-9e5f-fdad0ed4a7a3"     // string, testing agent-UUID string 4 RFC 4122 UUID e.g., see https://https://uuidgen.org/v/4
}

api-auth-data {
    "auth-token":
    "auth-token-type": value as stringauth-token-user-type: string (options: user, agent)
    auth-agent { 
        agent UUID - hashed value as string
    }
}

api-alert data {
    to_user: GUID as string
    alert_message: string
    alert_GMT_timestamp: datetime as string
    alert_locale: localedata as string
    alert_timezone: string
    alert_severity_level: integer as string
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
