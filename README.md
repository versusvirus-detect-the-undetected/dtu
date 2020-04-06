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

## API data type definition   

user data { 
    GUID (global user ID): string
    age - Integer value as string
    sex - string value (options “male”, “female”, "m", "f")
    geoposition-latitude: float value as string
    geoposition-longitude: float value as string
    geoposition-precision: integer as string
    diagnostics-has_cough: boolean as string
    diagnostics-has_fever: boolean as string
    diagnostics-fever-temperature: float as string
    diagnostics-has_taste_loss: boolean as string
    diagnostics-has_tested_positive: boolean as string
    diagnostics-is_immunized: boolean as string
}

api-auth-data {
    auth-token: value as string
    auth-token-user-type: string (options: user, agent, appliance)
}

type-auth-agent {
    agent GUID - hashed value as string
}

type-auth-appliance {
appliance GUID -hashed value as string

api-alert data {
    to_user: GUID as string
    alert_message: string
    alert_GMT_timestamp: datetime as string
    alert_locale: localedata as string
    alert_timezone: string
    alert_severity_level: integer as string
}

## API function calls

### get_latest_user_data(api-auth-data, GUID)

### get_user_ts_data(api_auth_data,GUID);

### get_users(api-auth-data, pagination as integer);

### get_user_dataset_list(api-auth-data, pagination as integer);

### push_user_alert(api-auth-data, GUID);

### create_user(api_auth_data)

