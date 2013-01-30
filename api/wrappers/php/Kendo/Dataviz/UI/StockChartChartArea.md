---
title: StockChartChartArea
slug: php-StockChartChartArea
tags: api, php
publish: true
---

# \Kendo\Dataviz\UI\StockChartChartArea

A PHP class representing the chartArea setting of StockChart.


## Methods

### background
The background color of the chart area.
#### Parameters

##### $value `string`



#### Example 
    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $chartArea->background('value');

### border

#### Parameters

##### $value `\Kendo\Dataviz\UI\StockChartChartAreaBorder|array`

The border of the chart area.


#### Example - using \Kendo\Dataviz\UI\StockChartChartAreaBorder

    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $border = new \Kendo\Dataviz\UI\StockChartChartAreaBorder();
    $color = 'value';
    $border->color($color);
    $chartArea->border($border);

#### Example - using array

    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $color = 'value';
    $chartArea->border(array('color' => $color));

### height
The height of the chart area.
#### Parameters

##### $value `float`



#### Example 
    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $chartArea->height(1);

### margin
The margin of the chart area.
#### Parameters

##### $value `float|`



#### Example  - using float
    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $chartArea->margin(1);

### opacity
The background opacity of the chart area.
#### Parameters

##### $value `float`



#### Example 
    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $chartArea->opacity(1);

### width
The width of the chart area.
#### Parameters

##### $value `float`



#### Example 
    $chartArea = new \Kendo\Dataviz\UI\StockChartChartArea();
    $chartArea->width(1);
