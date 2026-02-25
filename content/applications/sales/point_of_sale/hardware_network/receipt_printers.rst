================
Receipt printers
================

Receipt printers integrate with Point of Sale systems to receive print jobs directly from the POS.
Once properly configured and connected, this integration enables automatic receipt printing for
every completed transaction.

.. important::
   - Epson printers are strongly recommended. The following list presents the compatible printers
     with Odoo:

     - Network-based printers that support the ePOS communication protocol (without IoT), such as
       the TM-m30 iii (model 112 or 152).
     - ePOS printers with USB connectivity that need to be connected to an :doc:`IoT system
       </applications/general/iot/connect>`.
     - ESC/POS printers that require a connection via an :doc:`IoT box
       </applications/general/iot/iot_box>` using either a USB or network-based interface.
   - Bluetooth printers are not compatible with Odoo.

.. seealso::
   - `Receipt printers without IoT (video tutorial)
     <https://youtu.be/OUUi6N_xT-U?si=NZ9PPrsXDUcJ4kSy>`_
   - `Receipt printers with IoT (video tutorial)
     <https://youtu.be/ORojunUs5Bs?si=FrDJ0N-9f8SJlQrA>`_

.. _pos/epos-printers/configuration:

Configuration
=============

To configure the printer, plug it in and connect it with an Ethernet cable or to a Wi-Fi network.
Then, power the printer on; an automatic ticket with the printer’s IP address gets printed upon
connection. Keep the IP address in mind for the configuration process.

To link the printer with Point of Sale, follow the next steps:

#. Go to :menuselection:`Point of Sale --> Configuration --> Settings`.
#. Scroll down to the :guilabel:`Connected Devices` section and enable :guilabel:`ePos Printers`.
#. Type the IP address in the dedicated field.
#. Click :guilabel:`Save`.

Once the printer and Odoo are connected, ensure their connection is secure and reliable by
generating a :ref:`self-signed certificate <pos/epos-ssc/certificate>`. Alternatively, enable
:doc:`pos_lna` to allow Point of Sale to communicate directly with the printer on the same network.

.. seealso::
   - :doc:`pos_lna`
   - :doc:`epos_ssc`
   - :doc:`/applications/general/iot/devices/printer`

.. _pos/epos-printers/supported-printers:

Directly supported ePOS printers
================================

The **Epson TM-m30 i/ii/iii (Wi-Fi or Ethernet only) models** are strongly recommended, as they have
been fully tested with Odoo Point of Sale.

Other Wi-Fi or Ethernet Epson printer models that support the **ePoS protocol** should also be
compatible.

.. important::
   - The printer must be capable of operating in HTTP mode.
   - When using :doc:`Local Network Access (LNA) <pos_lna>`, the printer must have a **static
     IP address**; otherwise, it may become unreachable. The static IP should be configured
     through the router.

.. _pos/epos-printers/iot-supported-printers:

Printers with IoT system integration
====================================

The following printers require an :doc:`IoT system </applications/general/iot/devices/printer>` to
be compatible with Odoo:

- Epson TM-T20 family (incompatible ePOS software)
- Epson TM-T88 family (incompatible ePOS software)
- Epson TM-U220 family (incompatible ePOS software)

.. important::
   - Epson printers using Wi-Fi/Ethernet connections and following the `EPOS SDK Javascript protocol
     <https://download4.epson.biz/sec_pubs/pos/reference_en/technology/epson_epos_sdk.html>`_ are
     compatible with Odoo **without** an :doc:`IoT system
     </applications/general/iot/devices/printer>`.
   - Epson printers using only USB connections are compatible **with** an :doc:`IoT system
     </applications/general/iot/devices/printer>`.
   - Epson printers that connect via Bluetooth are **not compatible**.

.. _pos/epos-printers/troubleshooting:

Troubleshooting
===============

To resolve common hardware issues, including connectivity failures, configuration errors, and
physical maintenance, follow the instructions below:

- If the printer does not print the first automatic ticket with the IP address, check the network
  cable or Wi-Fi connection.
- If the receipt comes out blank, try flipping the paper roll; it may be upside-down.
- If the POS cannot connect to the printer, make sure the IP address introduced in Odoo matches the
  one on the first automatically printed ticket. Also, ensure the router gives the printer a static
  IP address.
- Check the printer's blinking lights to better identify the source of a problem.
