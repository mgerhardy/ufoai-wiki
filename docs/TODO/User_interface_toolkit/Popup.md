- `MN_InitPopup(name, title, text, button number)`
  - `name`: menu name, if we want to use another popup definition. Next
    functions will reuse the menu name defined here.
  - `button number`: number of button for the popup (0..3) to update the
    layout.
- `MN_InitPopupButton(num, label, tooltip, action)`
  - For each button we must call `MN_InitPopupButton`. Then it allow to
    use one call of `va` for each call.
- `MN_PushPopup(...)`
  - Yet not sure we should add this function.

Every param from this functions will be cloned. We dont need static
string for label, or command.

Example cp_installation_callback.c line 267:

    MN_InitPopup(NULL, _("Destroy Installation"), _("Do you really want to destroy this installation?"), 2);
    MN_InitPopupButton(0, _("Destroy"), _("Destroy installation"), command);
    MN_InitPopupButton(1, _("Cancel"), _("Forget it"), "mn_pop;");
    MN_PushPopup()

Then we also can take a look at `MN_PopupList` to see if we can do the
same (convert to MN_InitPopupList).

We should finally aim to allow multi instance of the same popup, but
it's not yet possible.


Wouldn't it be better to do something like popupButton_t
\*MN_PopupAddButton(name, title, text);?
--[Mattn](User:Mattn "wikilink") 06:30, 27 March 2009 (UTC)


Yes, we can, but the result should be a node_t. But it will not be a
real "add", i mean buttons are only visible or hiden.
[Bayo](User:Bayo "wikilink") 22:10, 27 March 2009 (UTC)