### Hide Pages From Navigation

Kentico DOES have a "Show in navigation" checkbox under Properties/Navigation/Basic properties. But to really make use of it, you have to add to the WHERE clause of your webparts:
```
DocumentMenuItemHideInNavigation = 0
```
...to exclude those items that are not checked.

Source: https://devnet.kentico.com/forums/f67/fp2/t41592/show-in-navigation-option-is-not-hiding-menu-it
