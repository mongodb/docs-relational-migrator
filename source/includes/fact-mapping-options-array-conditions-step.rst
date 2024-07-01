.. step:: (Optional) Array Conditions

   Allows you to sort an embedded array and limit the amount of entries in that array. There is also the option to just sort, and not apply a limit at all. When limiting to a single entry, there is the option to embed as a document instead of a single-element array.

   a. On the :guilabel:`Mappings` pane, click the :icon-fa5:`chevron-left` 
      icon next to :guilabel:`Advanced settings`.
   #. Select the :guilabel:`Add array conditions` :icon-fa5:`check-square` icon.
   #. Enter a filter in the :guilabel:`Value expression` text box.
   #. In the :guilabel:`Sort by and order` heading, select the source field to sort on and toggle between :icon-lg:`SortAscending` for ascending and :icon-lg:`SortDescending` for descending order.
   #. Select a :guilabel:`Limit` option: 

      - :guilabel:`No limit`: No limit
      - :guilabel:`Limit number of rows`: Enter the maximum number of elements returned in the array. Default vaulue is `10`.
      
   .. note::

      - Excluded fields cannot be sorted on. If a previously selected sorting field is excluded at a later point in time, the array condition is removed.
      - CDC updates and deletes will not be replaced.
