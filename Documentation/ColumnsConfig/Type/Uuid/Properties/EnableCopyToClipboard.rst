..  include:: /Includes.rst.txt

..  _columns-uuid-properties-enableCopyToClipboard:

=====================
enableCopyToClipboard
=====================

..  confval:: enableCopyToClipboard ('type' => 'uuid')

    :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
    :type: boolean
    :Scope: Display

    In case :php:`enableCopyToClipboard` is set to :php:`true`, which is the
    default, a button is rendered next to the input field, which allows to copy
    the UUID to the clipboard of the operating system.

    This column configuration can be overwritten by
    :ref:`page TSconfig <t3tsconfig:tceform>`.
