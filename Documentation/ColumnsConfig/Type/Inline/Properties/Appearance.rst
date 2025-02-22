.. include:: /Includes.rst.txt
.. _columns-inline-properties-appearance:

==========
appearance
==========

..  versionchanged:: 12.0
    The following properties have been removed:

    -   :php:`[appearance][headerThumbnail]`
    -   :php:`[appearance][fileUploadAllowed]`
    -   :php:`[appearance][fileByUrlAllowed]`

    Use the TCA column type :ref:`file <columns-file>` to handle files.

.. confval:: appearance (type => inline)

    :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
    :type: array
    :Scope: Display

    Has information about the appearance of child records, namely:

    collapseAll (boolean)
        Show all child records collapsed (if false, all are expanded)

    expandSingle (boolean)
        Show only one child record expanded each time. If a collapsed record is clicked, the currently
        open one collapses and the clicked one expands.

    showNewRecordLink (boolean)
        Disables the :guilabel:`New record` link in TCA `inline` elements without simultaneously disabling
        the :guilabel:`+` button in the header of each inline record (using
        :code:`['appearance']['enabledControls']['new']`).

    newRecordLinkAddTitle (boolean)
        Adds the title of the :ref:`foreign_table <columns-inline-properties-foreign-table>` to the "New record" link.

        false
         "Create new"
        true
         "Create new <title of foreign\_table>", e.g. "Create new address"

    newRecordLinkTitle (string or LLL reference)
        Overrides the title of the "New record" link with a localized string. This will work only if
        :code:`newRecordLinkAddTitle` is **not** set to true.

        Example::

            'newRecordLinkTitle' => 'LLL:EXT:myext/Resources/Private/Language/locallang_db.xlf:my_new_record_label'

    createNewRelationLinkTitle (string or LLL reference)
        Overrides the link text and title of the "Create new relation" button with a localised string.
        Only useful, if the element browser is enabled. This is usually used together with FAL relations to change it to "Add file" or similar.

    levelLinksPosition (string)
        Values: 'top' (default), 'bottom', 'both'. Defines where to show the "New record" link in relation
        to the child records. Value 'none' is no longer supported, use :code:`showAllLocalizationLink`,
        :code:`showSynchronizationLink` and :code:`showNewRecordLink` with value :php:`false` instead.

    useCombination (boolean)
        This is only useful on bidirectional relations using an intermediate table with attributes. In a "combination" it
        is possible to edit the attributes AND the related child record itself. If using a
        :ref:`foreign_selector <columns-inline-properties-foreign-selector>` in such a case, the
        :ref:`foreign_unique <columns-inline-properties-foreign-unique>` property  **must** be set to the same field as
        the :ref:`foreign_selector <columns-inline-properties-foreign-selector>`.

    suppressCombinationWarning (boolean)
        Suppresses the warning flash message that will be displayed when using **useCombination**.
        You can also override the message with your own message using the example below.

        Example::

            $GLOBALS['TCA']['tx_demo_domain_model_demoinline']['columns']['irre_records']['config'] = [
                 'appearance' => [
                    'overwriteCombinationWarningMessage' => 'LLL:EXT:demo/Resources/Private/Language/locallang_db.xlf:tx_demo_domain_model_demoinline.irre_records.useCombinationWarning',
                    'useCombination' => TRUE
                 ],
            ],

    useSortable (boolean)
        Activate drag & drop.

    showPossibleLocalizationRecords (boolean)
        Show unlocalized records which are in the original language, but not yet localized.

    showAllLocalizationLink (boolean)
        Defines whether to show the "localize all records" link to fetch untranslated records from the original language.

    showSynchronizationLink (boolean)
        Defines whether to show a "synchronize" link to update to a 1:1 translation with the original language.

    enabledControls (array)
        Associative array with the keys 'info', 'new', 'dragdrop', 'sort', 'hide', 'delete', 'localize'. If the accordant
        values are set to a boolean value (true or false), the control is shown or hidden in the header of each record.

    showPossibleRecordsSelector (boolean)
        Can be used to hide the foreign record selector from the interface, even if you have a
        :ref:`foreign_selector <columns-inline-properties-foreign-selector>` configured. This can be used to keep the
        technical functionality of the :ref:`foreign_selector <columns-inline-properties-foreign-selector>` but is useful
        if you want to replace it with your own implementation using a custom control,
        see :ref:`customControls <columns-inline-properties-customcontrols>`.

    elementBrowserEnabled (boolean)
        Hides or displays the element browser button in inline records
