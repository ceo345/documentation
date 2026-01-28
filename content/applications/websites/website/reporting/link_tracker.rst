============
Link tracker
============

The link tracker lets you create tracked links to measure your marketing campaigns'
effectiveness. They let you determine which channels bring you the most visitors and make informed
decisions.

Configuration
=============

The :guilabel:`Link Tracker` module is not installed by default. You need to enable the
:guilabel:`Email Marketing` option by going to :menuselection:`Website --> Configuration -->
Settings.` Alternatively, you can :doc:`install <../../../general/apps_modules>` the :guilabel:`Link
Tracker` module itself or one of the marketing apps.

Create a traceable URL
======================

To create and manage tracked links, navigate to :menuselection:`Website --> Site --> Link Tracker`.
Fill in the following information and click :guilabel:`Generate tracked link` to create a tracking
URL.

#. :guilabel:`URL`: The URL that is the target of the campaign. It is automatically populated with
   the URL used to access the menu.

#. :guilabel:`Campaign`: The specific campaign the link should be associated with. This parameter is
   used to distinguish the different campaigns.

#. :guilabel:`Medium`: The medium describes the category or method through which the visitor arrives
   at your site, such as organic search, paid search, social media ad, email, etc.

#. :guilabel:`Source`: The source identifies the specific platform or website that referred the
   visitor, such as a search engine, newsletter, or website.

.. image:: link_tracker/create-link-trackers.png
   :alt: Create a link tracker URL

The :guilabel:`Campaign`, :guilabel:`Medium`, and :guilabel:`Source` are called :abbr:`UTM (Urchin
Tracking Module)` parameters. They are incorporated in the tracked URL.

  .. tip::
     You can customize the :ref:`visibility <website/visibility/conditions>` of building blocks
     using the :abbr:`UTM (Urchin Tracking Module)` parameters, amongst other conditions.

Tracked links overview
======================

To get an overview of your tracked links, go to :menuselection:`Website --> Site --> Link Tracker`
and scroll down to :guilabel:`Your tracked links` section.

.. image:: link_tracker/your-tracked-link.png
   :alt: Get an overview of all the links you track.

Statistics
----------

To measure the performance of tracked links, click the track link and scroll down to the
:guilabel:`Statistics` section to get an overview of the number of clicks for the tracked links.
By default, the graph shows the total number of clicks. You can change the period to
:guilabel:`Last Month` or :guilabel:`Last Week` using the options on the right side of the heading.
