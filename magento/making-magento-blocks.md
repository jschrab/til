# Making Magento Blocks

Create/append to your “design/frontend/YOUR_PACKAGE/YOUR_THEME/layout/local.xml” a *reference* to the block you are creating.

```xml
<?xml version="1.0"?>
<layout version="0.1.0">
    <default>
      ...

      <!-- Is there a better way to do this? - JDS - 9-May-2016  -->
      <reference name="header">
          <block type="page/html" name="shoppingTools" template="page/html/shopping-tools.phtml"/>
      </reference>
      <reference name="root">
          <block type="page/html" name="shoppingTools" template="page/html/shopping-tools.phtml"/>
      </reference>
      <!-- Is there a better way to do this? - JDS - 9-May-2016  -->
    </default>

    ...
</layout>

```

The part I found confusing here was that ```<reference name="header">``` defines the layout level that your new block will be accessible from. But if you would like to have a block be accessible from multiple levels, that's something that currently isn't clear to me. This is why I defined two references but referred to the same .phtml template file.

Once this defined, cache cleared, one should be able to summon up the block in a template *that is a child of the reference* (root level or header, in the case above).

Source: http://inchoo.net/magento/how-to-add-currency-selector-to-magentos-header/
