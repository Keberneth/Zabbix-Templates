# Fortinet Zabbix Templates

This folder contains API-based Zabbix templates for monitoring Fortinet devices.
All templates use HTTP/REST API access for data collection.

## Included templates

- **FortiGate by HTTP**  
  Monitor FortiGate firewalls through the FortiGate API.

- **FortiADC by HTTP**  
  Monitor FortiADC appliances through the FortiADC API.

- **FortiSwitch by FortiGate HTTP**  
  Monitor FortiSwitch devices that are managed by a FortiGate controller.

- **FortiAP by FortiGate HTTP**  
  Monitor FortiAP devices that are managed by a FortiGate controller.

## How it works

- Monitoring is performed through API requests from Zabbix.
- No SNMP is required.
- The FortiSwitch and FortiAP templates are controller-side templates. They collect data from the FortiGate API instead of connecting directly to each switch or access point.
- When using the FortiGate-managed templates, link them to the same host as the FortiGate template so they can reuse the same API connection settings.

## Requirements

- Zabbix 7.0
- Network access from the Zabbix server or proxy to the Fortinet API endpoint
- A Fortinet API account or token with read access
- HTTPS access to the device management interface

## Basic setup

1. Import the required YAML template into Zabbix.
2. Configure the API connection macros on the host.
3. Link the template to the correct host.
4. Confirm that the API is reachable and that the credentials have the required permissions (Read).

## Notes

- These templates are designed to be simple and reusable.
- Available fields can vary between firmware versions, so small adjustments may be needed in some environments.
- Token-based API access is recommended where supported.

