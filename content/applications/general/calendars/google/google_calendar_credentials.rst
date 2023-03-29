=====================================
Synchronize Google Calendar with Odoo
=====================================

Synchronize Google Calendar with Odoo to see and manage meetings from both platforms (updates go in
both directions). This integration helps organize schedules so a meeting is never missed.

Setup in Google
===============

Select a project or create a project
------------------------------------

Create a new Google API project and enable the Google Calendar API. First, go to the
`Google API Console <https://console.developers.google.com>`_ and log into the Google account.

.. note::
   If this is the first time visiting this page, Google will prompt the user to enter a country and
   agree to the Terms of Service. Select a country from the drop-down list and agree to the
   :abbr:`ToS (Terms of Service)`.

Next, click :guilabel:`Select a project` and select or create an API project to configure OAuth in
and to store credentials. Click :guilabel:`New Project`.

.. image:: google_calendar_credentials/new-api-project.png
   :align: center
   :alt: Create a new API project to store credentials.

.. tip::
   Give the API Project a clear name like "Odoo Sync" so it can be easily identified.

Enable Google calendar API
--------------------------

Now, click on :guilabel:`Enabled APIs and Services` in the left menu. Select :guilabel:`Enabled APIs
and Services` again if the :guilabel:`Search bar` doesn't appear.

.. image:: google_calendar_credentials/enable-apis-services.png
   :align: center
   :alt: Enable APIs and Services on the API Project.

After that, search for *Google Calendar API* using the search bar and select :guilabel:`Google
Calendar API` from the search results. Click :guilabel:`Enable`.

.. image:: google_calendar_credentials/enable-google-cal-api.png
   :align: center
   :alt: Enable the Google Calendar API.

OAuth consent screen
--------------------

Now that the API project has been created OAuth should be configured. Click on :guilabel:`OAuth
consent` in the left menu and then select the :guilabel:`User Type`.

.. warning::
   Personal Gmail Accounts are only allowed to be :guilabel:`External` User Type, which means
   Google may require an approval or for :guilabel:`Scopes` to be added on. Using a Google WorkSpace
   account allows for :guilabel:`Internal` User Type. It should also be noted that while the API
   connection is in the :guilabel:`External` :guilabel:`Testing` mode then no approval is necessary
   from Google. User limits in this :guilabel:`Testing` mode is set to 100 users.

In the second step, :guilabel:`OAuth Consent Screen`, type *Odoo* in the :guilabel:`App name`
field, select the email address for the :guilabel:`User support email` field, and type the email
address for the :guilabel:`Developer contact information` section. Then, click :guilabel:`Save
and Continue`.

Skip the third step, :guilabel:`Scopes`, by clicking :guilabel:`Save and Continue`.

Next, if continuing in testing mode (External), add the email addresses being configured under the
:guilabel:`Test users` step by clicking on :guilabel:`Add Users` and then the :guilabel:`Save and
Continue` button. A summary of the :guilabel:`App registration` appears.

Finally, scroll to the bottom and click on :guilabel:`Back to Dashboard`.

Now the OAuth consent has been configured and it's time to create credentials.

Create credentials
------------------

The **Client ID** and the **Client Secret** are both needed to connect Google Calendar to Odoo. This
is the last step in the Google console, begin by clicking :guilabel:`Credentials` in the left menu.
Then click :guilabel:`Create Credentials` and select :guilabel:`OAuth client ID` Google will open a
guide to create credentials.

Under :guilabel:`OAuth Client ID`, select :guilabel:`Website application` for the
:guilabel:`Application Type` field and type *My Odoo Database* for the :guilabel:`Name`.

  - Under the :guilabel:`Authorized JavaScript Origins` section, click :guilabel:`+ Add URI` and
    type the company's Odoo full :abbr:`URL (Uniform Resource Locator)` address.

  - Under the :guilabel:`Authorized redirect URIs` section, click :guilabel:`+ Add URI` and type
    the company's Odoo :abbr:`URL (Uniform Resource Locator)` address followed by
    ``/google_account/authentication``. Finally, click :guilabel:`Create`.

.. image:: google_calendar_credentials/uri.png
   :align: center
   :alt: Add the authorized JavaScript origins and the authorized redirect URIs.

A :guilabel:`Client ID` and :guilabel:`Client Secret` will appear, copy these to a notepad.

Setup in Odoo
=============

Once the Client ID and the Client Secret are located, open the Odoo database and go to
:menuselection:`Settings --> General Settings --> Integrations --> Google Calendar`. Check the box
next to :guilabel:`Google Calendar`.

.. image:: google_calendar_credentials/settings-google-cal.png
   :align: center
   :alt: The Google Calendar checkbox in General Settings.

Next, copy and paste the Client ID and the Client Secret from the Google Calendar API Credentials
page into their respective fields below the :guilabel:`Google Calendar` checkbox. Then, click
:guilabel:`Save`.

Sync Calendar in Odoo
=====================

Finally, open the Calendar module in Odoo and click on the :guilabel:`Google` sync button to sync
Google Calendar with Odoo.

.. image:: google_calendar_credentials/sync-google.png
   :align: center
   :alt: Click the Google sync button in Odoo Calendar to sync Google Calendar with Odoo.

.. note::
   The first time syncing Google Calendar with Odoo, the page will redirect to the Google
   Account. Select the :menuselection:`Email Account` that should have access -->
   :menuselection:`Continue` (should the app be unverifed) --> :menuselection:`Continue` (to give
   permission for the transfer of data)

.. image:: google_calendar_credentials/trust-odoo.png
   :align: center
   :alt: Give Odoo permission to access Google Calendar.

Now, Odoo Calendar is successfully synced with Google Calendar!

.. warning::
   Odoo highly recommends testing the Google calendar synchronization on a test database and a
   test email address (that is not used for any other purpose) before attempting to sync the
   desired Google Calendar with the user's production database.

   Once a user synchronizes their Google calendar with the Odoo calendar:

   - Creating an event in Odoo causes Google to send an invitation to all event attendees.
   - Deleting an event in Odoo causes Google to send a cancellation to all event attendees.
   - Adding a contact to an event causes Google to send an invitation to all event attendees.
   - Removing a contact from an event causes Google to send a cancellation to all event attendees.

   Events can be created in Google Calendar without sending a notification by selecting
   :guilabel:`Don't Send` when prompted to send invitation emails.
