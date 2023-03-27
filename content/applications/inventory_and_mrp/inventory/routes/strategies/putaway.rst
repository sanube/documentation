<<<<<<< HEAD
=======================
Putaway Rules
=======================

A good warehouse implementation ensures that products automatically move to their appropriate
destination location. This process is seamless using Odoo's *Putaway rules*. Putaway is the process
of receiving shipments and putting products in appropriate locations.

=======
=============
Putaway Rules
=============

Defined by situations, conditions, and instructions, *Putaway rules* detail how incoming products
should be moved to specified locations. They are :ref:`push rules<inventory/routes/use_routes/push>`
triggered by the arrival of shipments in a certain location. The automatically generated rules
precisely instruct warehouse employees how and where to put away received products.

It is crucial when a warehouse contains volatile substances; putaway rules communicate the
importance that certain products cannot be stored in close proximity and minimize risks of chemical
reaction.
>>>>>>> ce24d81ba ([TAG] application/module: describe your changes in a short sentence)
If, for example, a warehouse contains multiple volatile substances that should not come into contact, it is crucial that these substances not be stored in close proximity to one another. Using putaway rules, it is possible to ensure that such products are stored in different locations.

Configuration
=============

Begin by navigating to :menuselection:`Inventory --> Configuration --> Settings`, then activate the
:guilabel:`Multi-Step Routes` checkbox under the :guilabel:`Warehouse` heading. By doing so, the
:guilabel:`Storage Locations` setting is automatically
enabled as well. Finally, click :guilabel:`Save`.

.. image:: putaway/multi-steps-routes.png
   :align: center
   :alt: Check multi-step routes box

Create a putaway rule
=====================

When a grocery store sells fruits and vegetables, products should be stored in different locations
depending on factors like frequency, size, product category, and specific environment needs.

Suppose the warehouse location :guilabel:`WH/Stock` contains two sub-locations
`WH/Stock/Vegetables` and `WH/Stock/Fruits`.

To manage where specific products are routed for storage, navigate to :menuselection:`Inventory -->
Configuration --> Putaway Rules`. Then, click on :guilabel:`Create` to configure a new putaway rule.
Choose the :guilabel:`Product` and/or :guilabel:`Product Category` that the rule will affect. Set
:guilabel:`When product arrives in` as the location where the rule will be triggered and
:guilabel:`Store to` as the location where products affected by the rule will be stored. Finally,
click :guilabel:`Save`.

.. note::
  It is also possible to create and manage putaway rules for a single product by going to the
  product page and clicking the :guilabel:`Putaway Rules` smart button at the top of the page.

.. image:: putaway/putaw2.png
   :align: center

.. note::
   The putaway rules can also be defined per product/product category, location, and package
   type (enable :guilabel:`Packages` in :menuselection:`Configuration --> Settings`). Define them
   through the :guilabel:`Smart Button` on each form.

.. note::
   If the location does not appear in the drop-down menu, add a new location in
   :menuselection:`Configuration --> Locations`. :guilabel:`Store to` locations can only be child
   locations of the location of origin.

Once a putaway rule has been configured, the product it specifies will be automatically routed to
the :guilabel:`Store to` location upon arriving in the :guilabel:`When product arrives in` location.
The summary of internal product movements can be viewed by selecting :menuselection:`Reporting -->
Product Moves` and enabling the :guilabel:`Internal` search filter on the :guilabel:`Filters`
dropdown under the :guilabel:`search bar` at the top of the page.

.. image:: putaway/putaw3.png
   :align: center
   :alt: Purchase order for apples and carrots

.. image:: putaway/putaw4.png
   :align: center

.. image:: putaway/putaw5.png
   :align: center

.. note::
   :guilabel:`Inventory Report` displays only :guilabel:`Product Types` with :guilabel:`Storable
   Product` as the value. To see how :guilabel:`Consumable Products` are moved using putaway rules,
   track them with :menuselection:`Reporting --> Product Moves`.