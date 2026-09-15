# Magento 2 Widget Parameters — utrzymywany fork (SISL)

Dodaje **bogatsze typy pól w konfiguracji widgetów** Magento 2. Standardowo parametr widgetu to
zwykły `text` — ten moduł dokłada trzy typy przydatne przy budowie widgetów z treścią:

- **WYSIWYG** — pełny edytor treści jako parametr widgetu (formatowanie, linki),
- **Textarea** — wieloliniowe pole tekstowe,
- **Image Chooser** — wybór obrazu z galerii mediów Magento zamiast wklejania ścieżki.

Dzięki temu własne widgety (bloki promocyjne, bannery, sekcje CMS) da się konfigurować wygodnie
z panelu, bez ręcznego wpisywania HTML-a czy ścieżek do plików.

To utrzymywany fork **zarchiwizowanego** `dmatthew/magento2-widget-parameters` (ostatni commit 2022).
Oryginał deklaruje `php ^7.1||^8.0` i nie ma przypiętego `magento/framework` — instaluje się „po cichu",
ale nie był testowany pod nowsze wydania. Ten fork doprecyzowuje zależności i jest zweryfikowany na
**Magento 2.4.9 / PHP 8.4** (di:compile + instancjacja komponentów modułu).

## Zgodność
- Magento **2.4.4 – 2.4.9** (Open Source / Adobe Commerce)
- PHP **8.1 – 8.4**
- `magento/framework >=103.0.4 <104`, `magento/module-cms >=104.0.0 <105`

## Instalacja

```bash
composer require sisl-source/magento2-widget-parameters
bin/magento module:enable Dmatthew_WidgetParameters
bin/magento setup:upgrade
bin/magento setup:di:compile   # tryb produkcyjny
```

## Jak używać
W definicji widgetu (`widget.xml` Twojego modułu) ustaw typ parametru na jeden z bloków renderujących:

```xml
<parameter name="content" xsi:type="block" visible="true" sort_order="10">
    <label>Treść</label>
    <block class="Dmatthew\WidgetParameters\Block\Adminhtml\Widget\Type\Wysiwyg"/>
</parameter>
```
Dostępne klasy: `...\Widget\Type\Wysiwyg`, `...\Widget\Type\Textarea`, `...\Widget\Type\ImageChooser`.
Po tej zmianie edytor pojawia się w formularzu konfiguracji widgetu (Content → Widgets).

## Licencja
MIT (jak oryginał). Fork utrzymywany przez [SISL](https://sisl.pl).
