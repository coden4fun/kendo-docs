---
title: Button
slug: php-ui-button
tags: api, php
publish: true
---

# \Kendo\UI\Button

A PHP wrapper for Kendo UI [Button](/api/web/button).

Inherits from [\Kendo\UI\Widget](/api/wrappers/php/Kendo/UI/Widget).

## Usage

To use Button in a PHP page instantiate a new instance, configure it via the available
configuration [methods](#methods) and output it by `echo`-ing the result of the [render](/api/wrappers/php/Kendo/UI/Widget#render) method.

### Using Kendo Button

    <?php
    // Create a new instance of Button and specify its id
    $button = new \Kendo\UI\Button('Button');

    // Configure it
    $button->enable(true)

    // Output it

    echo $button->render();
    ?>


## Methods

### click
Fires when the Button is clicked with the mouse, touched on a touch device, or ENTER (or SPACE) is pressed while the Button is focused.
For additional information check the [click](/api/web/button#events-click) event documentation.

#### Returns
`\Kendo\UI\Button`

#### Parameters

##### $value `string|\Kendo\JavaScriptFunction`

#### Example - using string which defines a JavaScript function

    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->click('function(e) { }');
    ?>

#### Example - using string which defines a JavaScript name
    <script>
        function onClick(e) {
            // handle the click event.
        }
    </script>
    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->click('onClick');
    ?>

#### Example - using [\Kendo\JavaScriptFunction](/api/wrappers/php/kendo/javascriptfunction)

    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->click(new \Kendo\JavaScriptFunction('function(e) { }'));
    ?>

### enable
Indicates whether the Button should be enabled or disabled. By default, it is enabled, unless a disabled="disabled" attribute is detected.

#### Returns
`\Kendo\UI\Button`

#### Parameters

##### $value `boolean`



#### Example 
    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->enable(true);
    ?>

### imageUrl
Defines a URL, which will be used for an img element inside the Button. The URL can be relative or absolute. In case it is relative, it will be evaluated with relation to the web page URL.The img element can be added automatically by the widget, or an existing element can be used, if it has a k-image CSS class applied.

#### Returns
`\Kendo\UI\Button`

#### Parameters

##### $value `string`



#### Example 
    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->imageUrl('value');
    ?>

### spriteCssClass
Defines a CSS class (or multiple classes separated by spaces), which will be used for a span element inside the Button with a background image.
In case you want to use an icon from the Kendo UI theme sprite background image, you need to define two classes - k-icon and the respective icon CSS class.The span element can be added automatically by the widget, or an existing element can be used, if it has a k-sprite CSS class applied.

#### Returns
`\Kendo\UI\Button`

#### Parameters

##### $value `string`



#### Example 
    <?php
    $button = new \Kendo\UI\Button('Button');
    $button->spriteCssClass('value');
    ?>
