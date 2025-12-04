=======
Croatia
=======

E-invoicing via mojeRačun
=========================

Odoo can connect to the national eRačun platform via third-party provider `mojeRačun
<https://moj-eracun.hr>`_ to send and receive e-invoices.

To make use of this integration, an account and `invoice package
<https://portal.moj-eracun.hr/podrska/cjenik/>`_ from mojeRačun are needed. The rest of this
documentation assumes that one has already been obtained.

.. _croatia/configuration:

Configuration
-------------

Follow these steps to set up e-invoicing via mojeRačun in Odoo.

.. _croatia/configuration/company:

Company configuration
~~~~~~~~~~~~~~~~~~~~~

Go to :menuselection:`Accounting --> Configuration --> Settings` and scroll down to
:guilabel:`MojEracun E-invoicing`. Fill the :guilabel:`Username` field with the numeric username and
the :guilabel:`Password` field with the password provided by mojeRačun.

.. note::
   Alternatively, the :guilabel:`Username` can be set to the e-mail address used to register on
   mojeRačun.

Ensure that the :guilabel:`Company ID (OIB or GIN)` and :guilabel:`Company Business Unit (PJ)`
fields are correctly filled in, matching the data used to register on mojeRačun.

:guilabel:`Business Software (ERP) ID` should be set to `Saodoo-001`.

Optionally, specify the :guilabel:`Incoming E-Invoices Journal` where invoices received via MER
should be created. If left unset, the default purchase journal will be used.

Set the :guilabel:`MojEracun Operating Mode` to :guilabel:`Production` to send and receive invoices
on the production network.

Then click :guilabel:`Activate` to activate the connection with mojeRačun.

.. _croatia/configuration/journal:

Journal configuration
~~~~~~~~~~~~~~~~~~~~~

Go to :menuselection:`Accounting --> Configuration --> Journal` and click the :guilabel:`Customer
Invoices` journal to open its configuration.

In the :guilabel:`Fiscalization (HR)` section, fill the :guilabel:`Business premises label`,
:guilabel:`Issuing device label`, :guilabel:`Business premises label (refund approval)`, and
:guilabel:`Issuing device label (refund approval)` fields.

The :guilabel:`Business premises label` and :guilabel:`Issuing device label` are used to generate
invoice names. The :guilabel:`Business premises label (refund approval)` and :guilabel:`Issuing
device label (refund approval)` fields are used to generate credit note names.

.. _croatia/sending:

Sending an e-invoice
--------------------

The following invoice fields should be set before sending to mojeRačun.

.. _croatia/sending/invoice-name:

Invoice name
~~~~~~~~~~~~

Ensure the invoice name is in the format
`{Journal code}-{Year}-{Sequence}/{Business premises label}/{Issuing device label}`. To let Odoo
automatically create the invoice name in this format, perform the :ref:`journal configuration
<croatia/configuration/journal>` as explained above before creating the first invoice.

Product configuration
~~~~~~~~~~~~~~~~~~~~~

Set the :guilabel:`KPD category` on every invoice line.

.. tip::
   The :abbr:`KPD category (Klasifikacija proizvoda po djelatnostima)` can also be set on the
   product, in order to be automatically applied on invoice lines when the product is used. To do
   so, go to :menuselection:`Accounting -> Customers -> Products`, click the product, and set the
   :guilabel:`KPD category`.

Business process type
~~~~~~~~~~~~~~~~~~~~~

In the :guilabel:`Croatia: Fiscalization 2.0` tab, set the :guilabel:`Business Process Type` as
appropriate. If :guilabel:`P99: Customer-defined process` is selected, fill the :guilabel:`Custom
Process Name`.


Fiscal user and operator OIB
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Croatian government expects the user who sends the invoice to be identified via their personal
:abbr:`OIB (Osobni identifikacijski broj)` number. The fiscal user defaults to the user who confirms
the invoice and is identified in the :guilabel:`Croatia: Fiscalization 2.0` tab under
:guilabel:`Fiscal User`.

The user's OIB can be set on the user's contact. To do so, go to :menuselection:`Accounting ->
Configuration -> Settings -> General Settings -> Manage Users`, click the user in the list, click
:guilabel:`Related Partner`, and set the :guilabel:`Personal OIB`.

.. seealso::
   :ref:`accounting/e-invoicing/generation`

Invoice fiscalization information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After the invoice has been sent, the fiscalization status, fiscalization request ID, reported
payment status, and mojeRačun internal ID may be viewed in the :guilabel:`Croatia:
Fiscalization 2.0` tab.


Fetching status updates
~~~~~~~~~~~~~~~~~~~~~~~

Once an invoice has been sent, Odoo periodically checks for any updates to the invoice's status
(e.g. rejection by MER, the eRačun system, or by the recipient). To manually check for updates,
go to the :menuselection:`Accounting` dashboard, and in the :guilabel:`Vendor Bills` journal, click
the :guilabel:`MER: Fetch status` button.

Reporting a payment
~~~~~~~~~~~~~~~~~~~

The Croatian government expects to be notified once payment has been received for an invoice. To
send this notification, click the :guilabel:`MER: Report payments` button on the invoice view, which
appears if the invoice has unreported payments.

.. _croatia/receiving:

Receiving e-invoices
--------------------

Odoo periodically checks for new invoices received via mojeRačun. New invoices received via
mojeRačun appear in the :guilabel:`Incoming E-Invoices Journal` specified in the :ref:`settings
<croatia/configuration/company>`.

Rejecting an invoice
~~~~~~~~~~~~~~~~~~~~

To reject an incoming invoice, click the :guilabel:`MER: Reject eRacun` button on the invoice view.
This notifies the eRačun system and the sender that the invoice is rejected.

.. seealso::
   :doc:`Odoo electronic invoicing in Croatia
   <../accounting/customer_invoices/electronic_invoicing/croatia>`

