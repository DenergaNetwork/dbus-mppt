dbus-mppt
===========

This application reads essential data from a Morningstar Tristar MPPT charge controller and sends it on the D-Bus. It is currently designed to run on the Victron Color Control (CCGX) but can easily be modified to run on other systems.


Running the application on CCGX
===============================

The application expect the IP-address/hostname and the Modbus IP-port number stored in the CCGX settings. You can either edit the /data/conf/settings.xml file manually (not recommended) or use the CCGX settings menu. To use the settings menu copy the file PageSettingsTsmppt.qml in the qml folder to the folder on CCGX where the qml files are stored (usually /opt/color-control/gui/qml). Then add a link to PageSettingsTsmppt.qml in the main settings qml-file, PageSettings.qml found in the same folder:

    MbSubMenu {
        description: qsTr("TriStar MPPT 60 Solar Charger")
        subpage: Component { PageSettingsTsmppt {} }
    }

Change "TriStar MPPT 60" to "TriStar MPPT 45" or "TriStar MPPT 30" according to the Tristar MPPT version you have.

To display the data in the CCGX gui you also need to add these lines to the isModelSupported function in PageSolarCharger.qml:

    /* Morningstar TriStar MPPT */
    if (productId.value === 0xABCD)
        return true



The README.md of localsettings contains some information on how to run localsettings on linux.

