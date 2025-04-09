WMI is a powerful interface in Windows that can be used for retrieving various information about Windows components, services, state and software installed.

# Zabbix Template for Basic Windows WMI Queries

This Zabbix template provides a set of items to monitor basic Windows operating system information using WMI (Windows Management Instrumentation) queries. It is designed to be a simple starting point for monitoring Windows servers and workstations.

## Template Contents

The "WMI Querys" template includes the following items:

* **WMI: Operating System Caption:** Retrieves the descriptive name of the operating system (e.g., "Microsoft Windows Server 2019 Standard").
* **WMI: Free Disk Space on C: Drive (GB):** Monitors the free space on the C: drive in gigabytes (GB).
* **WMI: Last Boot Time:** Retrieves the date and time of the last system boot.
* **WMI: Operating System Service Pack:** Displays the installed Service Pack version (if applicable).
* **WMI: OS Install Date:** Retrieves the date and time when the operating system was installed.
* **WMI: Operating System Architecture:** Indicates the operating system architecture (e.g., "64-bit").
* **WMI: Operating System Version:** Displays the main version of the operating system (e.g., "10.0").

![{BFB5C107-A015-4E31-87D4-E7E23EA676E3}](https://github.com/user-attachments/assets/50dc7941-43e2-4431-abb9-7ab3e84926e8)

.....

All items have a data collection interval of **5 minutes**. Historical data is not saved (`trends: '0'`) for text items (Caption, Last Boot Time, Service Pack, Install Date, Architecture, Version) to save space in the Zabbix database. Disk free space does store trends for analysis over time.

## How to Use This Template

1.  **Download the content of the `WMI_Querys_for_Windows.yaml` file**. This file contains the XML export of the Zabbix template.
2.  **Import the template into your Zabbix server:**
    * Navigate to the `Configuration` -> `Templates` section in the Zabbix web interface.
    * Click the `Import` button in the upper right corner.
    * Select the `WMI_Querys_for_Windows.txt` file and click `Import`.
3.  **Link the "WMI Querys" template to the Windows hosts you want to monitor:**
    * Navigate to the `Configuration` -> `Hosts` section.
    * Find the Windows host to which you want to apply the template.
    * Go to the `Templates` tab.
    * In the `Link new templates` field, start typing "WMI Querys" and select it.
    * Click the `Add` button.
    * Click the `Update` button at the bottom.
4.  **Ensure that the Zabbix Agent is installed and configured correctly** on the monitored Windows hosts. The agent must be able to execute WMI queries. By default, the standard agent configuration allows this.
5.  **Verify the data:** After linking the template, go to the `Monitoring` -> `Latest data` section to ensure that the items are collecting information correctly.

## Considerations

* **Dependencies:** This template has no dependencies on custom scripts or additional `UserParameter` configurations. It utilizes the built-in WMI capabilities of the Zabbix Agent.
* **Customization:** You can modify the data collection interval (`delay`) according to your needs. You can also add triggers to generate alerts based on the values of these items (e.g., an alert if disk free space is low).
* **Expansion:** This is a basic template. You can expand it by adding more items to monitor other aspects of the Windows operating system using different WMI queries. Consult the WMI documentation to explore the numerous available classes and properties.
* **Performance:** WMI queries generally have a low impact on system performance, but if you plan to add a large number of WMI items with very frequent collection intervals, consider the potential performance impact.

## Contributions

If you wish to improve this template or add more features, contributions are welcome! You can follow the general contribution steps described in the main repository `README.md` to create forks and submit Pull Requests.

This template provides a solid foundation for Windows monitoring with Zabbix using the powerful capability of WMI queries.
