TC_BCH_BLE_01
=============

RQ reference
------------

CH1.3_2.3, CH1.3_2.5, CH1.3_2.6, AD-BTSSP1.1_3.3

Test Purpose
------------

ensure that
{
when {the DUT reads a Handover Select Message with Bluetooth Low Energy carrier information records or a single Carrier Configuration Record from a not-paired device}
then {the DUT shall successfully pair with this device}
}

Comments
--------

Connection handover to a BLE carrier using Security Manager OOB required data types defined in AD-BTSSP1.1_3.3

Selection
---------

Devices which support Bluetooth Low Energy

Test Configuration Functions
----------------------------

Conditions
----------

The RS is a BLE device in Peripheral Role with an NFC Forum Tag which contains a Handover Select Message for a BLE carrier with carrier information records as defined in CH1.3 section 2.5 and AD-BTSSP1.1 section 3.3.

Test case scenario
------------------

* Configure following data on the RS: NDEF Handover Select Message as described in conditions
* When the configured NDEF message is read by an NFC Forum device in Poll mode, the RS starts advertisement on the BLE carrier in connectable mode
* The RS accepts a BLE Connection Request from DUT
* The RS accepts a BLE Pairing Request from DUT

Acceptance criteria
-------------------
The DUT pairs with the RS

Scenario 	TC_BCH_BV_01.A Static Connection Handover to a BLE carrier
--------------------------------------------------------------------------

==== ========= =========
Step Direction Exchanges
==== ========= =========
1    DUT<-     NFC: Handover Select NDEF Message shown in Table 1
2    DUT<-     BLE: advertising
3    DUT->     BLE: Connection Request
4    DUT<-     BLE: Connection Response
5    DUT->     BLE: Pairing (using “Just Works” method)
==== ========= =========
