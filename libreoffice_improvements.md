# Writer

## activate the ribbon interface equivalent

One first need to activate the experimental features

go to `options` -> `libreoffice` (the first one) -> `advanced` -> `activate experimental features`

Then one can activate the ribbon layout (or one of the various other layouts available)

go to `view` -> `toolbar layout` and pick one

It is fully ready for writer, but not complete for the other tools of the suit

# Use the copy and paste of text formatting

This is one of the weird design choices of libreoffice.

1) select the text to use as the source of the formatting
2) click on the `paste format` icon
3) press `Ctrl` while selecting the text to re-format

The requirement of pressing `Ctrl` is due to the various options that are available in the pasting, and the default one is different from what one would expect.

Basically, if only a portion of a paragraph has a weird format, it is considered *character format* and is pasted, but if the whole paragraph has the same format then is a *paragraph format* and requires the `Ctrl` hotkey to be activated.

see: https://help.libreoffice.org/Common/Copying_Attributes_With_the_Format_Paintbrush
