---
title: kendo.diagram.shape
meta_title: API Reference for methods, objects and properties in the Shape - diagram's primitive
meta_description: Examples and detailed explanation of Kendo UI methods and properties.
slug: api-framework
tags: api,framework
publish: false
---

# kendo.diagram.shape

The Shape object represents a visual node in the graph or diagram.

## Configuration

### id `String`

The unique identifier for a Shape. Makes it easy to find the Shape by ID using the Diagram API.

### path `String`

The path option of a Shape is a description of a custom geometry. The format follows the standard SVG format (http://www.w3.org/TR/SVG/paths.html#PathData "SVG Path data.").

#### Example - custom Shape data

The following Shape creation defines a Path visual and the data string defines a custom Path (here the 'Apple' logo).

    diagram.addShape(new Point(100, 100), {
        path:"m52.10522,2.5c-11.76762,2.1674 -15.67321,12.01996 -15.82503,17.64957c6.47508,0.468 10.51705,-3.18687 12.17056,-5.32507c2.69337,-3.03252 3.35037,-7.30312 3.65446,-12.32449l0,0zm1.44453,19.46323c-8.50652,-0.0042 -13.2543,3.47298 -15.59565,3.51137c-2.68627,-0.20935 -10.51538,-3.35788 -15.0796,-3.40794c-15.98605,0.47638 -20.56654,17.84731 -20.36841,25.31639c1.3023,28.59586 18.7516,35.97569 21.6031,36.66646c2.28713,0.4505 9.999,-3.52641 15.67194,-3.3454c6.19436,0.64577 10.52249,3.21524 13.00983,3.03589c3.14639,-0.21855 13.41026,-8.51358 16.5041,-21.29358c-6.23814,-5.27423 -10.08575,-10.0545 -10.4303,-14.59035c-0.15976,-2.05142 2.92491,-13.64513 7.8441,-16.90373c0.70998,-4.00609 -6.59648,-9.09009 -12.32408,-8.97577c-0.28196,-0.00751 -0.5606,-0.01334 -0.83505,-0.01334l0,0z" }
    );

### stroke `Object`

Defines the stroke configuration.

### stroke.color `String` *(default: "Black")*

Defines the color of the shape's stroke.

#### Example - setting the shape's stroke and strokeWidth

    diagram.addShape(new Point(100, 100), {
        type:"circle",
        stroke: {
            color: "violet",
            width: 3
        }
    });

### stroke.width `Number` *(default: 1)*

Defines the thickness or width of the shape's stroke.

### stroke.dashType `String`

The dash type of the shape.

The following dash types are supported:

* "dash" - a line consisting of dashes
* "dashDot" - a line consisting of a repeating pattern of dash-dot
* "dot" - a line consisting of dots
* "longDash" - a line consisting of a repeating pattern of long-dash
* "longDashDot" - a line consisting of a repeating pattern of long-dash-dot
* "longDashDotDot" - a line consisting of a repeating pattern of long-dash-dot-dot
* "solid" - a solid line

#### Example - setting the dash type

    diagram.addShape(new Point(100, 100), {
        stroke: {
            color: "green",
            dashType: "dot",
            width: 3
        }
    });

### type `String` *(default: "rectangle")*

Specifies the type of the Shape using any of the built-in shape type.

* "rectangle": this is the default option, representing a SVG Rectangle
* "circle" : a SVG circle/ellipse

#### Example - creating an elliptic shape

    diagram.addShape(new Point(100, 100), {
        type:"circle",
        width:200,
        height:100
    });

### x `Number` *(default: 0)*

Defines the x-coordinate of the shape when added to the diagram.

### y `Number` *(default: 0)*

Defines the y-coordinate of the shape when added to the diagram.

### minWidth `Number` *(default: 20)*

Defines the minimum width the shape should have, i.e. it cannot be resized to a value smaller than the given one.

### minHeight `Number` *(default: 20)*

Defines the minimum height the shape should have, i.e. it cannot be resized to a value smaller than the given one.

### width `Number` *(default: 100)*

Defines the width of the shape when added to the diagram.

### height `Number` *(default: 100)*

Defines the height of the shape when added to the diagram.

### background `String` *(default: "SteelBlue")*

Defines the fill-color of the shape.

### shapes.hover `Object`

Defines the hover configuration.

### shapes.hover.background `String` *(default: "#70CAFF")*

Hover's background color.

### connectors `Array`

Defines the connectors the shape owns.

* "top" - top connector.
* "right" - right connector.
* "bottom" - bottom connector.
* "bottomRight" - bottom right connector.
* "left" - left connector.
* "auto" - auto connector.

You can easily define your own custom connectors or mix-match with the above defined custom connectors.

Example - custom shape with custom connectors

The following defines a custom shape with connectors adapted to the shape's outline. Note in particular the various helpful methods (right(), left(), top()) to define positions relative to the shape.

![Custom connectors on custom shape.](../../../getting-started/dataviz/diagram/ThreeWayShape.PNG)

    $("#diagram").kendoDiagram({
        shapes: [{
            path: "m1,53.69333l17.5647,-17.56445l0,8.78235l23.15292,0l0,-26.34678l-8.78181,0l17.56417,-17.56444l17.5647,17.56444l-8.78238,0l0,26.34678l23.15297,0l0,-8.78235l17.56473,17.56445l-17.56473,17.56466l0,-8.78231l-63.87057,0l0,8.78231l-17.5647,-17.56466l0,0z",
            connectors: [{
                name: "Upstream",
                position: function(shape) {
                    return shape.transformPoint(shape.bounds().top());
                }
            }, {
                name: "SideLeft",
                position: function(shape) {
                    var p = shape.bounds().left();
                    return shape.transformPoint(new kendo.diagram.Point(p.x, p.y+17));
                }
            }, {
                name: "SideRight",
                position: function(shape) {
                    var p = shape.bounds().right();
                    return shape.transformPoint(new kendo.diagram.Point(p.x, p.y + 17));
                }
            }]
        }]
    });

### connectors.connector `Object`

### connectors.connector.position `String`

### connectors.connector.description `String`

### rotation `Object`

### rotation.angle `Number` *(default: 0)*

![alt Attention](http://demos.telerik.com/aspnet-ajax/toolbar/examples/overview/Img/followUp.gif "We need to look into this.") *this is an object right now and contains only an angle*

### content `String`

Sets the text content of the Shape.

Example - setting the text

     var shape = diagram.addShape(new Point(100, 100),{
                        content: "Telerik"
                    });
    // setting it explicitly in the options
    shape.options.content = "Kendo UI";
    shape.redraw();

    // or in one go by passing the settings
    shape.redraw({content:"JustTrace"});

### bounds `Object`

![alt Attention](http://demos.telerik.com/aspnet-ajax/toolbar/examples/overview/Img/followUp.gif "We need to look into this.") *all bounds should be merged*

## Methods

### position

Get/set method returning the current global position or sets the position specified.

#### Parameters

##### point `Point|Undefined`

Either the location to set or if no parameter given returns the current location.

### triggerBoundsChange

![alt Attention](http://demos.telerik.com/aspnet-ajax/toolbar/examples/overview/Img/followUp.gif "We need to look into this.") *private?*

### clone

Returns a clone (with a different id) of the shape.

### visualBounds

### rotatedBounds

### select

Selects or deselects the shape.

#### Parameters

##### value `Boolean`

Use 'true' to select the shape or 'false' to deselect it.

### rotate

### connections

Returns the connections attached to the shape. You can optionally specify to return only the incoming or outgoing connections.

#### Parameters

##### type `String`

If not parameter specified all connections are returned, if "in" then only the incoming (i.e. towards the shape) are returned, if "out" the only the outgoing (i.e. away from the shape) are returned.

##### Example - counting in/out connections

This will print the incoming (20), outgoing (20) and all (40) connections. The first incoming connection's stroke color is turned red.

    var shape = diagram.addShape(new Point(100, 100));
    var rightConnector = shape.getConnector("Right");
    var leftConnector = shape.getConnector("Left");
    for(var k = 0; k< 20; k++){
        diagram.connect(rightConnector, new Point(300, k * 20));
        diagram.connect(new Point(0, k * 20), leftConnector);
    }
    console.log("incoming: " + shape.connections("in").length);
    console.log("outgoing: " + shape.connections("out").length);
    console.log("all: " + shape.connections().length);

    var connection = shape.connections("in")[0];
    connection.redraw({ stroke: { color: "red" } });

### refreshConnections

Calls the Connection.refresh() method on all attached connection.

### getConnector

Fetches a (default or custom) Connector defined on the Shape by its name.

##### Example - changing a Connector color after the shape was created

    var s = diagram.addShape(new Point(100, 100),
                            {
                                data      : "circle",
                                width     : 200,
                                height    : 100,
                                connectors: [
                                    {
                                        name       : "Top",
                                        description: "Top Connector"
                                    }
                                ]
                            });
                    var c = s.getConnector("Top");
                    c.options.background = "red";



### getPosition

Returns the middle positions of the sides of the bounds or the center of the shape's bounds. This method is useful when defining custom connectors where a position function relative to the shape's coordinate system is required.

#### Parameters

##### side `String`

One of the four sides of a bound; "left", "right", "top", "bottom". If none specified the center of the shape's bounds will be returned.

##### Example - a custom connector positioned near the center

This custom shape has only one connector slightly offset from the center of the shape.

    var shape = new kendo.diagram.Shape(
        { "connectors": [{
            name: AUTO,
            Description: "Auto Connector",
            position: function (shape) {
                var center = shape.getPosition("center");
                return new Point(center.x + 15, center.y);
            }
        }]
        });

### redraw

Renders the shape with the given options. It redefines the options and redraws the shape accordingly.

##### Example - change the shape's background color

    var shape = diagram.addShape();
    shape.redraw({background: "Green"});

