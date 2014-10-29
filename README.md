# AeroGear Push Notification Message Sender

Service for sending push notification messages via AeroGear. See http://aerogear.org/docs/unifiedpush/push-message-format/ for more details

# Environment Variables

The following Environment variables are supported/required by this service:

* `AEROGEAR_SERVER_URL`: Required - The URL of the AeroGear instance to use - e.g.  `https://aerogear.rhcloud.com/ag-push/`
* `AEROGEAR_APPLICATION_ID`: Required - The Unique Application Id of the AeroGear app - e.g.  `12345678-1234-1234-1234-1234567890ab`
* `AEROGEAR_MASTER_SECRET`: Required - The Master Secret Key of the AeroGear app - e.g. `12345678-1234-1234-1234-1234567890ab`
* `AEROGEAR_TTL`: Optional - The Time to Live value for the submitted notification - default value = 3600


# Group Send Message API

# send [/send]

'Send Message' endpoint.

## send [POST]

'Send Message' endpoint.

+ Request (application/json)
    + Body
            {
              "message" : {
                "alert": "The message to send (REQUIRED)",
                "sound": "The sound to use on device when the message is received (OPTIONAL - default value = 'default')",
                "badge": "Numeric value for the badge to use (OPTIONAL - default value = 2)",
                "contentAvailable": "true|false - iOS specific argument to mark the payload as ‘content-available’ (OPTIONAL - default value = true)",
                "actionCategory": "iOS8 feature for interactive notifications (OPTIONAL - omitted if absent)",
                "customKey": "some custom value (OPTIONAL - omitted if absent)",
                "anotherCustomKey":"some other custom value (OPTIONAL - omitted if absent)"
              }
            }

+ Response 200 (application/json)
    + Body
            {
              "status": "ok"
            }

+ Response 400 (application/json)
    + Body
            {
              "status": "error",
              "message": [
                {
                  "param": "The parameter which caused the validation error",
                  "msg": "The validation error message"
                }
                ...
              ]
            }
