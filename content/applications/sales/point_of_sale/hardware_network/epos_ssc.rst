.. _epos_ssc/ePOS printers:

=========================================
Self-signed certificate for ePOS printers
=========================================

To work with Odoo, some printer models that can be used without an :doc:`IoT system
</applications/general/iot>` may require the HTTPS protocol to establish a secure connection
between the browser and the printer. However, trying to reach the printer's IP address using HTTPS
results in a warning page in most web browsers. Force the connection to establish an HTTPS link and
enable the printer in Odoo.

.. important::
   Since the `Chromium 142 update <https://developer.chrome.com/release-notes/142>`_, using a
   self-signed certificate is no longer required. The recommended approach is to use the
   :doc:`Local Network Access <pos_lna>` method instead.

.. _pos/epos-ssc/certificate:

Generation, export, and import of self-signed certificates
==========================================================

Printers that operate without an :doc:`IoT box </applications/general/iot/iot_box>` still require
secure communication, achieved by generating a self-signed certificate.

.. important::
   - Generating an self-signed certificate should only be done **once**. Creating another
     certificate causes devices using the previous one to lose HTTPS access.
   - Printers that use an :doc:`IoT box </applications/general/iot/iot_box>` do not need a
     self-signed certificate, as the IoT box generates it automatically.
   - For stable results, it is strongly recommended to use the Google Chrome browser to generate
     the self-signed certificate.

.. note::
   - To export self-signed certificates from an operating system or a web browser that has not been
     mentioned in this documentation, search for `export SSL certificate` + `the name of your
     browser or operating system` in the preferred search engine.
   - Similarly, to import SSL certificates from an unspecified OS or browser, search for `import SSL
     certificate root authority` + `the name of your browser or operating system` in the preferred
     search engine.

.. tabs::

   .. tab:: Windows 10 & Linux OS

      .. tabs::

         .. tab:: Generate a self-signed certificate

            To generate a self-signed certificate on **Google Chrome**, follow the next steps:

            #. Open the browser, type the printer’s IP address in the search bar (e.g.,
               `https://192.168.1.25`), and press `Enter`.
            #. On the security warning page, click :guilabel:`Advanced`, then :guilabel:`Proceed to
               [IP address] (unsafe)` to force the connection.
            #. On the EPSON homepage, follow these steps:

               #. Click :guilabel:`Advanced Settings`, then :guilabel:`Administrator Login` to log
                  in to the printer's homepage.
               #. Paste the initial password located behind the printer in the :guilabel:`Current
                  Password` field, then press `Enter`.
               #. On the EPSON platform, go to :menuselection:`Network Security --> SSL/TLS -->
                  Certificate`.
               #. On the :guilabel:`Certificate` page, click :guilabel:`Update` under the
                  :guilabel:`Self-signed Certificate` section.
               #. Adapt the :guilabel:`Common Name` field to retain only the IP address, then click
                  :guilabel:`Next`, then :guilabel:`OK`. Wait for the printer’s lights to stop
                  blinking.

            .. image:: epos_ssc/browser-https-insecure.png
              :alt: Warning page about the connection privacy on Google Chrome
              :scale: 75 %

            .. note::
               The Epson homepage may vary depending on the printer model used. For the Epson TM-m30
               ii, log in to the Epson homepage by typing `epson` as the username and the printer's
               serial number as the password.

         .. tab:: Export a self-signed certificate

            The export process is heavily dependent on the :abbr:`OS (Operating System)` and the
            browser. Start by accessing the printer settings on a web browser by navigating to its
            IP address (e.g., `https://192.168.1.25`). Then, force the connection as explained in
            the :guilabel:`Generate a self-signed certificate` tab.

            To export the certificate on **Google Chrome**, follow the next steps:

            #. Once the printer’s lights are solid, hover the mouse over the browser’s search bar
               and click :guilabel:`Not secure`, then :guilabel:`Certificate details`.
            #. Click the :guilabel:`Details` tab in the :guilabel:`Certificate Viewer` popover,
               then click :guilabel:`Export`.
            #. Add `.crt` next to the IP address in the :guilabel:`File name` field.
            #. Set the :guilabel:`Save as type` field to `Base64-encoded ASCII, single certificate`.
            #. Click :guilabel:`Save`.

            To export the certificate on **Mozilla Firefox**, follow the next steps:

            #. Click :guilabel:`Not secure` next to the search bar.
            #. Go to :menuselection:`Connection not secure --> More information`.
            #. Click :guilabel:`View certificate` in the :guilabel:`Security` tab, then
               :guilabel:`Details`.
            #. Select the certificate, click :guilabel:`Export`, then select a folder in your local
               drive.
            #. Click :guilabel:`Close`.

         .. tab:: Import a self-signed certificate

            The import process is heavily dependent on the :abbr:`OS (Operating System)` and the
            browser.

            .. tabs::

               .. tab:: Windows 10

                  To import a self-signed certificate from **Google Chrome**:

                  #. Open the browser.
                  #. Go to :menuselection:`Settings --> Privacy and security --> Security`, and
                     click :guilabel:`Manage certificates`.
                  #. Click :guilabel:`Manage imported certificates from Windows` on the
                     :guilabel:`Certificate Manager` page.
                  #. Click :guilabel:`Import` in the :guilabel:`Certificates` popover.
                  #. Follow the next steps in the :guilabel:`Certificate Import Wizard`:

                     #. Click :guilabel:`Next`, then :guilabel:`Browse` to select the certificate,
                        then click :guilabel:`Next` again.
                     #. Select the :guilabel:`Place all certificates in the following store` option.
                     #. Click :guilabel:`Browse`, select the :guilabel:`Trusted Root Certification
                        Authorities` folder, and click :guilabel:`OK`.
                     #. Click :guilabel:`Next`, then :guilabel:`Finish`.
                  #. Click :guilabel:`Yes` in the :guilabel:`Security Warning` popover.

               .. tab:: Linux

                  To import a self-signed certificate from **Google Chrome**:

                  #. Open the browser.
                  #. Go to :menuselection:`Settings --> Privacy and security --> Security`, and
                     click :guilabel:`Manage certificates`.
                  #. Click :guilabel:`Installed by you` under the :guilabel:`Custom` section on the
                     :guilabel:`Local certificates` tab.
                  #. Click :guilabel:`Import` next to :guilabel:`Trusted Certificates`, and select
                     the exported certification file from your local drive.
                  #. Accept all warnings.
                  #. Click :guilabel:`ok`.


                  To import a self-signed certificate from **Mozilla Firefox**:

                  #. Open the browser.
                  #. Go to :menuselection:`Settings --> Privacy & Security --> Security --> View
                     Certificates`.
                  #. In the :guilabel:`Certificate Manager` popover, click the :guilabel:`Your
                     Certificates` tab, then :guilabel:`Import`, and select the certificate in your
                     local drive.
                  #. Click the :guilabel:`Servers` tab in the :guilabel:`Certificate Manager`
                     popover.
                  #. Click :guilabel:`Add Exception`.
                  #. Enter the printer's IP address in the :guilabel:`Location` field, then
                     click :guilabel:`Get Certificate`.
                  #. Enable the :guilabel:`Permanently store this exception` option and confirm.

   .. tab:: Mac OS

      .. tabs::

         .. tab:: Generate a self-signed certificate

            To generate a self-signed certificate using the `Keychain Access
            <https://support.apple.com/en-gb/guide/keychain-access/kyca8916/mac>`_ app on Mac,
            follow the next steps:

            #. Access the :guilabel:`Keychain Access` app on Mac.
            #. Go to :menuselection:`Access --> Certificate Assistant --> Create a Certificate`.
            #. Enter a name for the certificate.
            #. Select an identity type, then the type of certificate.
            #. Click :guilabel:`Create`.
            #. Review the certificate, then click :guilabel:`Done`.

         .. tab:: Export a self-signed certificate

            To export a self-signed certificate from **Google Chrome**:

            #. Open the browser, type the printer’s IP address in the search bar (e.g.,
               `https://192.168.1.25`), and press `Enter`.
            #. On the security warning page, click :guilabel:`Advanced`, then :guilabel:`Proceed to
               [IP address] (unsafe)` to force the connection.
            #. Click :guilabel:`Not secure` next to the search bar, then :guilabel:`Certificate is
               not valid`.
            #. Go to the :guilabel:`Details` tab and click :guilabel:`Export`.
            #. Add `.crt` at the end of the file name to ensure it has the correct extension.
            #. Select :guilabel:`Base64-encoded ASCII, single certificate`, at the bottom of the
               popover.
            #. Click :guilabel:`Save`.

            To export the certificate on **Mozilla Firefox**, follow the next steps:

            #. Click :guilabel:`Not secure` next to the search bar.
            #. Go to :menuselection:`Connection not secure --> More information`.
            #. Click :guilabel:`View certificate` in the :guilabel:`Security` tab, then
               :guilabel:`Details`.
            #. Select the certificate, click :guilabel:`Export`, then select a folder in your local
               drive.
            #. Click :guilabel:`Close`.

   .. tab:: Android OS

      To import a self-signed certificate into an Android device, first create and export it from a
      computer. Next, transfer the `.crt` file to the device via email, Bluetooth, or USB. Once
      the file is on the device, follow the next steps:

      #. Go to the device settings.
      #. Type `certificate` in the search bar.
      #. Click :guilabel:`Certificate AC`, then :guilabel:`Install from device storage`.
      #. Select the certificate file to install it on the device.

      .. Note::
         - The specific steps for installing a certificate may vary depending on the Android version
           and the device manufacturer.
         - Install the EPSON ePOS SDK for JavaScript on each mobile device if required.
         - Download the certificate on a computer if the tablet restricts direct downloads. Forward
           the file via email, then open it directly from the tablet to complete the installation.

   .. tab:: iOS

      To import a self-signed certificate into an iOS device, first create and export it from a
      computer. Then, transfer the `.crt` file to the device via email, Bluetooth, or any
      file-sharing service.

      Downloading this file triggers a warning popover. Click :guilabel:`Allow` to download the
      configuration profile, and close the second popover. Then follow the next steps:

      #. Go to the **Settings** app on the iOS device.
      #. Click :guilabel:`Profile Downloaded` under the user's details box.
      #. Locate the downloaded `.crt` file and select it.
      #. Click :guilabel:`Install` in the top-right corner.
      #. Enter a passcode if needed.
      #. Click :guilabel:`Install` in the top-right corner of the certificate warning screen and
         the popover.
      #. Click :guilabel:`Done`.

      The certificate is installed, but needs to be authenticated:

      #. Go to :menuselection:`Settings --> General --> About > Certificate Trust Settings`.
      #. Enable the installed certificate using the :icon:`fa-toggle-on` (switch) toggle.
      #. Click :guilabel:`Continue` in the popover.

Certificate import verification
===============================

To confirm the printer's connection is secure, connect to its IP address using HTTPS. For example,
navigate to `https://192.168.1.25` in a browser. If the self-signed certificate has been applied
correctly, no warning page appears, and the address bar should display a padlock icon, indicating a
secure connection.
