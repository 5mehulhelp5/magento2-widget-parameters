# Magento 2 Widget Parameters — maintained fork (SISL)

Adds **richer field types to Magento 2 widget configuration**. By default a widget parameter is a
plain `text` field — this module adds three types that are handy when building content widgets:

- **WYSIWYG** — a full content editor as a widget parameter (formatting, links),
- **Textarea** — a multi-line text field,
- **Image Chooser** — pick an image from the Magento media gallery instead of pasting a path.

This makes custom widgets (promo blocks, banners, CMS sections) comfortable to configure from the
admin, with no hand-written HTML or file paths.

This is a maintained fork of the **archived** `dmatthew/magento2-widget-parameters` (last commit
2022). The original declares `php ^7.1||^8.0` and pins no `magento/framework` — it installs
"silently" but was never tested against newer releases. This fork tightens the dependencies and is
verified on **Magento 2.4.9 / PHP 8.4** (di:compile + instantiation of the module's components).

## Compatibility
- Magento **2.4.4 – 2.4.9** (Open Source / Adobe Commerce)
- PHP **8.1 – 8.4**
- `magento/framework >=103.0.4 <104`, `magento/module-cms >=104.0.0 <105`

## Installation

```bash
composer require sisl-source/magento2-widget-parameters
bin/magento module:enable Dmatthew_WidgetParameters
bin/magento setup:upgrade
bin/magento setup:di:compile   # production mode
```

## How to use
In your module's widget definition (`widget.xml`) set the parameter type to one of the rendering blocks:

```xml
<parameter name="content" xsi:type="block" visible="true" sort_order="10">
    <label>Content</label>
    <block class="Dmatthew\WidgetParameters\Block\Adminhtml\Widget\Type\Wysiwyg"/>
</parameter>
```
Available classes: `...\Widget\Type\Wysiwyg`, `...\Widget\Type\Textarea`, `...\Widget\Type\ImageChooser`.
After this change the editor shows up in the widget configuration form (Content → Widgets).

## License
MIT (same as upstream). Fork maintained by [SISL](https://sisl.pl).

---

### Maintained by SISL

Maintained fork by **[SISL](https://sisl.pl)** — [Magento 2 development and modules](https://sisl.pl/moduly-magento). More self-hosted plugins: [SISL Marketplace](https://sisl.pl/sklep).