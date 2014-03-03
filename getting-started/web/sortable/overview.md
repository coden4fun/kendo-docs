---
title: Overview
meta_title: Documentation for Sortable widget in Kendo UI framework
meta_description: How to use the Sortable widget.
slug: gs-web-sortable-overview
relatedDocs: api-web-sortable
tags: getting-started, web
publish: true
---

# Sortable Overview

> Sortable is available in [Q1 2014 Beta](http://demos.telerik.com/kendo-ui/Beta/web/sortable/index.html)

The **Sortable** widget makes a group of DOM elements sortable by dragging and dropping with mouse/finger.

## Getting Started

### Initialize the Sortable using a jQuery selector

    <ul id="sortable">
        <li>Item1</li>
        <li>Item2</li>
        <li>Item3</li>
    </ul>

    <script>
        $("#sortable").kendoSortable();
    </script>

## Placeholder

Placeholder is the element which indicates where the dragged item will be placed after drop. By default the placeholder is a clone of the dragged element with removed `id` attribute and visibility set to hidden. Developer have the ability to change the default placeholder though the `placeholder` configuration option.

> **Important** Placeholder element is appended to the Sortable's DOM element. This is why jQuery's `index` method might return incorrect results. When the developer wants to find the index of a given item inside the Sortable collection it is recommended to use widget's [`indexOf`](../../../api/web/sortable#methods-indexof) method.

### Set the placeholder to a function

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>
    
    <script>
        $("#sortable").kendoSortable({ 
            placeholder: function(element) {
                return element.clone().css({
                    "opacity": 0.3,
                    "border": "1px dashed #000000"
                });
            }
        });
    </script>

### Set the placeholder to a string

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>
    
    <script>
        $("#sortable").kendoSortable({ 
            placeholder: "<li>Drop Here!</li>"
        });
    </script>

## Hint

Hint is the element which represents the dragged. By default the hint is a clone of the dragged. Developer have the ability to change the default hint though the `hint` configuration option.

> **Important** Hint element is appended to the `<body>` element. This might cause styling issues if the CSS rules are applied only to the Sortable's element.

### Set the hint to a function

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>
    
    <script>
        $("#sortable").kendoSortable({ 
            hint: function(element) {
                return $("<span></span>")
                        .text(element.text())
                        .css("color", "#FF0000");
            }
        });
    </script>

### Set the hint to a string

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>
    
    <script>
        $("#sortable").kendoSortable({ 
            hint: "<span>hint!</span>"
        });
    </script>

### Disabling the hint

The Sortable widget can operate without hint. To disable the hint you should set it to an empty function ([jQuery.noop](http://api.jquery.com/jQuery.noop/)).

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>
    
    <script>
        $("#sortable").kendoSortable({ 
            hint: $.noop
        });
    </script>

## Filter/Disable items

The **filter** option specifies which items inside the Sortable's element will be sortable. Items that does not match the filter selector will not be draggable nor reordered when user drags a sortable item over them.

The **disabled** option specifies which items inside the Sortable's element cannot be dragged. Items that match the disabled selector cannot be dragged but will reorder when user drags a sortable item over them.

### Disable all items at runtime

    <ul id="sortable">
        <li>ItemA1</li>
        <li>ItemA2</li>
        <li>ItemA3</li>
    </ul>

    <button id="btnDisable">Disable</button>
    
    <script>
        $("#sortable").kendoSortable({ 
            disabled: ".disabled"
        });

        $("#btnDisable").click(function() {
            $("#sortable").children().addClass("disabled");
        });
    </script>

## Movement by axis

By default the widget uses mouse cursor to determine the drop target before/after which sorted item should be placed. This means that if the mouse cursor is not over the target sortable element the placeholder will not be re-positioned.

If the `axis` is set to "x" or "y" however, the widget will start operating in movement by axis mode - the widget will use x/y position of the mouse cursor to determine the current target. To see this feature in action please check [constraints demo page](http://demos.telerik.com/kendo-ui/web/sortable/constraints.html).

## Accessing an Existing Sortable


You can reference an existing **Sortable** instance via
[jQuery.data()](http://api.jquery.com/jQuery.data/).

### Accessing an existing Sortable instance

    var sortable = $("#sortable").data("kendoSortable");
