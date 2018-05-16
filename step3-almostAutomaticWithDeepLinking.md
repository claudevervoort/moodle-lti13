# Pick a Tool Descriptor using deep linking

While the activation flow greatly simplifies the deployment of a tool, user must still be
able to be communicated some instructions; if the tool has distinct URLs for its placements,
or custom parameters, etc... the proper configuration is still tricky and error prone.

What if we could get a tool descriptor that lays out the configuration of the tool so that
all that settings can be pre-populated? To pick that descriptor, rather than inventing a new
flow, the proposal is to introduce a new type to Deep Linking, the `toolDescriptor` type.

## Ad-hoc or LTI App Store

The deep linking flow can be:

- **ad-hoc**: User pastes a URL and Moodle jumps to that tool. The returned response is not
expected to be signed.
- **app store**: The model can be extended to deploy app stores. User jumps to the app
store to pick an app. The app store is a specific kind of LTI tool.

The 1st iteration will be to support the ad-hoc model.

## Deep Linking flow

The deep linking [request](examples/deepLinkingRequestForTool.json) is sent with only one
type of content that can be returned, the tool descriptor:

```json
  "http://purl.imsglobal.org/spec/lti-dl/claim/deep_linking_settings": {
    "accept_types": ["https://moodle.org/ltiapp"],
    "accept_multiple": false,
    "auto_create": false
  }
```

The [response](examples/deepLinkingResponse.json) contains the tool descriptor.

```json
    "https://purl.imsglobal.org/spec/lti-dl/claim/content_items": [
        {
            "type": "https://moodle.org/ltiapp",
            "url": "https://virtualgarden.example.com",
            "ltiversion": "1.3.0",
            "alg": [
                "RS256"
            ],
            "logo_uri": "/assets/vg.png",
            "name": "Virtual Garden",
            "name#fr": "Jardin Virtuel",
            "description": "A garden simulator, only missing the fresh air.",
            "description#fr": "Un jardin virtuel, il ne manque que l'air frais",
            "placements": {
                "contentselector": {
                    "url": "/deeplinking"
                }
            },
            "scopes": [
                "https://purl.imsglobal.org/spec/lti-ags/scope/lineitem",
                "https://purl.imsglobal.org/spec/lti-ags/scope/result.readonly",
                "https://purl.imsglobal.org/spec/lti-ags/scope/score"
            ],
            "privacy": [
                "email"
            ],
            "jwks": {
                "keys": [
                    {
                        "alg": "RS256",
                        "kty": "RSA",
                        "use": "sig",
                        "n": "yeNlzlub94YgerT030codqEztjfU_S6X4DbDA_iVKkjAWtYfPHDzz_sPCT1Axz6isZdf3lHpq_gYX4Sz-cbe4rjmigxUxr-FgKHQy3HeCdK6hNq9ASQvMK9LBOpXDNn7mei6RZWom4wo3CMvvsY1w8tjtfLb-yQwJPltHxShZq5-ihC9irpLI9xEBTgG12q5lGIFPhTl_7inA1PFK97LuSLnTJzW0bj096v_TMDg7pOWm_zHtF53qbVsI0e3v5nmdKXdFf9BjIARRfVrbxVxiZHjU6zL6jY5QJdh1QCmENoejj_ytspMmGW7yMRxzUqgxcAqOBpVm0b-_mW3HoBdjQ",
                        "e": "AQAB",
                        "kid": "NjVBRjY5MDlCMUIwNzU4RTA2QzZFMDQ4QzQ2MDAyQjVDNjk1RTM2Qg"
                    }
                ]
            },
            "activationUrl": "/deploy?dl=a783djf2"
        }
```