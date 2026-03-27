FortiGate-controller templates for managed FortiSwitch and FortiAP
================================================================

Files
-----
- FortiSwitch by FortiGate HTTP.yaml
- FortiAP by FortiGate HTTP.yaml

Intended use
------------
Link these templates to the same FortiGate host that already uses your "FortiGate by HTTP" template.
They reuse the same macros:
  {$FGATE.API.FQDN}
  {$FGATE.API.PORT}
  {$FGATE.API.TOKEN}
  {$FGATE.SCHEME}
  {$FGATE.DATA.TIMEOUT}
  {$FGATE.HTTP.PROXY}

Quick endpoint checks
---------------------
Replace FQDN, PORT and TOKEN with your values.

curl -sk "https://FQDN:PORT/api/v2/monitor/switch-controller/managed-switch?access_token=TOKEN" | jq .
curl -sk "https://FQDN:PORT/api/v2/cmdb/switch-controller/managed-switch?access_token=TOKEN" | jq .
curl -sk "https://FQDN:PORT/api/v2/cmdb/wireless-controller/wtp?access_token=TOKEN" | jq .
curl -sk "https://FQDN:PORT/api/v2/monitor/wifi/client?access_token=TOKEN&global=1" | jq .

Notes
-----
- The templates are controller-side. They talk to the FortiGate, not directly to the FortiSwitch or FortiAP.
- The FortiSwitch template normalizes inventory/status fields from:
    /api/v2/monitor/switch-controller/managed-switch
    /api/v2/cmdb/switch-controller/managed-switch
- The FortiAP template normalizes inventory/client fields from:
    /api/v2/cmdb/wireless-controller/wtp
    /api/v2/monitor/wifi/client
    /api/v2/monitor/wifi/client/select
- Fortinet field names can vary between FortiOS releases. The master JavaScript items intentionally try several common field names.
- If one specific field does not populate on your build, inspect the master item JSON and adjust the related dependent item's JSONPath or the JavaScript normalization.

Direct-device API options
-------------------------
- FortiAP supports its own REST API on the AP itself.
- FortiSwitch also has its own REST API, but it is a separate device-side management plane and does not reuse the FortiGate token.
