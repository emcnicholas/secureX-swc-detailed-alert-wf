# secureX-swc-detailed-alert-wf

This Cisco SecureX orchestration workflow is very similar to my ["Stealthwatch Cloud - Webex Teams Alerts"](https://github.com/emcnicholas/secureX-swc-wxt-alert-wf) workflow. In this workflow we are only creating a custom Webex Teams message for the **Inbound Port Scanner** alerts, but also creating a generic alert message for all other Alert Types. The idea here is to get started with creating more detailed alerts messages for attacks that mean more to your organization, while still have the generic alerts for all others, until a customized message is needed.

## SecureX Stealthwatch Cloud Detailed Alert Workflow

**Prerequisites:**
1. Cisco Stealthwatch Cloud (SWC) Account (and API key)
2. Cisco SecureX Account (and API key)
3. Cisco Webex Teams Account (and API key)

## Installation Steps
Please follow the below steps exactly to get started!

1. Browse to your SecureX orchestration instance. This wille be a different URL depending on the region your account is in: 

* US: https://securex-ao.us.security.cisco.com/orch-ui/workflows/
* EU: https://securex-ao.eu.security.cisco.com/orch-ui/workflows/
* APJC: https://securex-ao.apjc.security.cisco.com/orch-ui/workflows/

2. Click on **IMPORT** to import the workflow:

![](screenshots/import-workflow.png)

3. Click on **Browse** and copy paste the content of the [SecureX Cloud Analytics Demo Workflow Shared.json](https://raw.githubusercontent.com/emcnicholas/secureX-swc-detailed-alert-wf/main/SecureX%20Cloud%20Analytics%20Demo%20Workflow%20Shared.json) file inside of the text window. 

![](screenshots/copy-paste.png)

4. Click on **IMPORT**.

5. Next we will need to fill some API keys and details before we can run this workflow. 
    * **SWC_Target** On the main page of Orchestration, go to **Targets**, select **SWC_Target**, and change the host to your endpoint.
    * **swc_api_key** In the **SecureX Cloud Analytics Demo** workflow global workflow properties, scroll down to **Variables**, select the **swc_api_key** variable, and enter your API key in the Value field and save.
    * **wxt_access_token** Select the **wxt_access_token** variable, and enter your token in the Value field and save.
    * **wxt_room_id** Select the **wxt_room_id** variable, and enter your Webex Teams room id in the Value field and save.

> **Note:** make sure not to select an activity when looking for the global workflow properties.

> **Note:** Please retrieve your Webex key from: [https://developer.webex.com/docs/api/getting-started](https://developer.webex.com/docs/api/getting-started). Please be aware that the personal token from the getting started page only works for 12 hours. Please follow these steps to request a "bot" token: https://developer.webex.com/docs/integrations.

> **Note:** Please retrieve the Webex room ID now. You can create a new space or find an existing one via these link: retrieve the Room ID from: https://developer.webex.com/docs/api/v1/rooms/list-rooms. You can also add the roomid@webex.bot bot to the room and it will send you the roomId in a private message and then remove itself from the room.

9. Now it is time to test, click on **RUN** in the top right of your window, and eveyrhting shopuld be working now. If not try troubleshooting by click on the activity that is colored red. 

![](screenshots/run.png)

10. As a final step you could choose to enable to scheduled trigger for this workflow. This is recommended, as the workflow only retrieves the security events of the last hour. By scheduling it, the Security analysts will be updated every hour for potential new malicious activity. To enable the trigger, click on the hyperlink below and uncheck the `DISABLE TRIGGER` checkbox. This can be found in the workflow properties in the right menu pane. 

![](screenshots/schedule.png)

> **Note:** make sure not to select an activity when looking for the global workflow properties.

## Notes

* Please test this properly before implementing in a production environment. This is a sample workflow!
* The roadmap will include a webhook based trigger, instead of a scheduled run. 

## Author(s)

* Ed McNicholas (Cisco)
* Christopher van der Made (Documentation Only) (Cisco)


