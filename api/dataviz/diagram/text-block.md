---
title:kendo.dataviz.diagram.TextBlock
slug:api-dataviz-diagram-text-block
publish: true
---

### kendo.dataviz.diagram.TextBlock

This represents a non-wrapping text element.

## Configuration

##### Example - adding a text element to the background canvas

This will add a text element underneath the diagram in the canvas.

    diagram.canvas.append(
        new kendo.diagram.TextBlock(
        {   text:"Kendo diagrams",
            x:200,
            y:50,
            fontFamily: "Tahoma",
            fontSize: 25,
            background: "SteelBlue"
        })
        );

### Rectangle

This represents a standard rectangle.

##### Example - creating a simple bar-chart in a custom shape

This example creates a databound, custom shape with Rectangle primitives into a simple bar chart.

![Simple bar chart using rectangles.](ChartShape.PNG)

    var getVisual = function(data)
    {
        var g = new kendo.diagram.Group({
            autoSize: true
        });
        var r = new kendo.diagram.Rectangle({
            width : 100,
            height: 80,
            background: "white",
            stroke: {
                color: "dimGray"
            }
        });
        g.append(r);
        var d = data.data;
        if(d){
            for(var k=0;k< d.length; k++){
                var color= d[k]<40? "green":"red";
                g.append(new kendo.diagram.Rectangle({x: 10+k*12, y: 60- d[k], height:d[k], width:10, background:color}));
            }
        }

        var fn = new kendo.diagram.TextBlock({
            text: data.name,
            fontSize: 11,
            fontFamily:"Segoe UI",
            background:"gray",
            x   : 30,
            y   : 13
        });
        g.append(fn);
        return g;
    }
    var options = {
        dataSource: [
            {
                "name" : "Josh K.",
                "data" : [10.5, 44.1, 33.7, 12.0, 23.9 ],
                "items": [
                    {"name": "Anna W.", "data": [7.5, 24.4, 13.0, 40.9, 13.1 ]},
                    {"name": "Jeff L.", "data": [20.5, 34.7, 43.7, 42.0, 3.9 ]}
                ]
            }
        ],
        autoBind  : true,
        visualTemplate: getVisual
    };
    diagram = $("#canvas").kendoDiagram(options).data("kendoDiagram");

    diagram.layout({type:"Tree", subtype:"MindmapHorizontal"});

### Path

This represents a path with a path definition following the SVG 1.1 standard.


### Marker

This represents an adorning element of a Path visual, an arrow head in particular. To define a marker on a Path you need both the assignment to the Path and the addition to the definition section (the <defs/> section)of the underlying SVG root. The Canvas element has an addMarker method which does take care of this however.

### Line

This represents a single, straight line segment.

### Polyline

This represents a straight, multi-point line.

### Image

This represents an image.

### Group

This represents an invisible, grouping element with visual children. Groups can be nested to form a hierarchy.

### Circle

This represents an ellipse or circle.

### Canvas


This is a wrapper around the SVG root which defines various utility methods and properties to easily add and manipulate elements (markers, visual, positions and so on).



## Transformations

See also the Matrix and MatrixVector objects in the Maths documentation.

### Scale

### Translation

### Rotation

### CompositeTransform



----------


# kendo.dataviz.ui.diagram Math and related

Kendo diagram contains various structures and utilities related to transformations of visuals, geometry, graph analysis and graph layout. A detailed explanation of all structures and methods would go well beyond the scope of this help, you can find additional information in these sources:

-  [the official SVG 1.1 documentation](http://www.w3.org/TR/SVG/coords.html "the official SVG 1.1 documentation")
-  [graph drawing and graph analysis on Wikipedia](http://en.wikipedia.org/wiki/Graph_drawing "Graph drawing and graph analysis")
-  [an introduction to networks](http://www.amazon.com/Networks-An-Introduction-Mark-Newman/dp/0199206651/ "An introduction to networks")
-  [introductory graph theory](http://www.amazon.com/Introductory-Graph-Theory-Gary-Chartrand/dp/0486247759 "Introductory graph theory")
-  [graph drawing: algorithms for the visualization of graphs](http://www.amazon.com/Graph-Drawing-Algorithms-Visualization-Graphs/dp/0133016153 "Graph drawing: algorithms for the visualization of graphs")

## HashTable

Represents a collection of key-value pairs (called buckets) stored in a classic array with the hash of the key used to identify uniquely the buckets. Because the buckets are accessed through their hash value it's important you use the appropriate add/remove methods to access them.

Internally the buckets look like

    [hashOfKey] <=> {key: givenKey, value: givenValue }

and you can add, remove or retrieve these like so

    var ht = new HashTable();
    ht.add(givenKey, givenValue);
    var obj = ht.get(givenKey);
    var theValue = obj.value;
    ht.remove(givenKey);

where the key and value can be arbitrary values or objects.

### add
Adds a key-value pair to the table. The key/value can be objects or values (number or string). Adding a pair with an existing key will overwrite the stored object.

### set
Sets or adds the key-value pair.

### get
Returns the bucket (not the value) with the given key. No exception is thrown if the key is not present, null is returned.

### remove
Removes the bucket with the given key (see the example code above). No exception is thrown if the key is not present.

### containsKey
Returns whether the given key exists in the table.

### forEach
Loops over the buckets in the hashtable (the key/value are not given as parameters but as one key-value object!).

    ht.forEach(function(obj){
        var key = obj.key;
        var value = obj.value;
    })

###clone
Returns a (shallow) clone of the HashTable.

## Set

A set only contains once a particular item, contrasting other data structure allowing repeated occurrences.

    var set = new Set();
    set.add("some element");
    set.add("some element"); // will not be added since items in a set appear only once

You can pass a Dictionary or a HashTable in the constructor, it will populate the Set with the key-value buckets defined by these structures;

    var dic = new Dictionary();
    dic.add("k1", "Telerik");
    var set = new Set(dic);
    set.forEach(
        function(kv){
            var key = kv.key; // "k1"
            var value = kv.value; // "Telerik"
        }
    );
The Set structure is based internally on the HashTable and thus has the same characteristics. The Set specific methods are the following;

### toArray
Returns an array of the elements contained in the Set.

### forEach
The for-each loops over the items and not the buckets as is the case with the HashTable. Internally the Set items are both key and value of a key-value pair of the HashTable.

## Dictionary

The dictionary or map is a key-value store where the key is unique. In practice a dictionary is more common than a HashTable but they share a lot of functionality, the Dictionary is in fact based on the HashTable.

The add/remove/set methods are similar to the HashTable, the Dictionary adds to this;

### forEachKey

A loop over the keys of the dictionary.

    var dictionary = new Dictionary();
    dictionary.forEachKey(function(key){...});

### forEachValue

A loop over the values in the dictionary.

    var dictionary = new Dictionary();
    dictionary.forEachValue(function(value){...});

### forEach
Loops over the key-value pairs, handed over as paramters;

    var dictionary = new Dictionary();
    dictionary.forEach(function(key, value){...});

### keys
Returns an array of the dictionary keys.

## Queue

The queue is a first-in first-out structure with objects being added using the Enqueue method and objects being fetched through the Dequeue method.  Only the top objects in the queue can be fetched.

### Enqueue

Enqueues an objects in the queue.

### Dequeue

Fetches the top-most item from the queue.

## Range

The Range object is effectively an array of equally separated numbers. This separation defaults to either one in case the start-value is less than the stop-value or minus one otherwise.

    var r1 = new diagram.Range(10, 20); // the array [10, 11, .., 20]
    var r2 = new diagram.Range(20, 10); // the array [20, 19, .., 10]
    var r3 = new diagram.Range(20, 10, -2); // the array [20, 18, .., 10]

## Matrix

The Matrix object is an abstraction of the transformation matrix as used in SVG. The 3x3 matrix contains only six elements which are denoted by `a, b, c, d, e, f` and are organized as

    |a c e|
    |b d f|
    |0 0 1|

This means that the matrix can also be represented a 6-tuple or vector `[a, b, c, d, e, f]` which you can create using the MatrixVector class. Various methods are available which allow you to go back and forth between these two classes.

Special cases of the Matrix and MatrixVector are:

      |1 0 tx|
      |0 1 ty|  <=> [1 0 0 1 tx ty] <=> translation (tx, ty)
      |0 0  1|

      |sx 0 0|
      |0 sy 0|  <=> [sx 0 0 sy 0 0] <=> scaling (sx, sy)
      |0  0 1|

      |cos(a) -sin(a) 0|
      |sin(a) cos(a)  0|  <=> [cos(a) sin(a) -sin(a) cos(a) 0 0] <=> roation with angle a (radians)
      | 0      0      1|

### plus
Adds another matrix to the current one, i.e. the standard matrix addition. This modifies the current matrix and does not return a new instance.

### minus
Substracts the given matrix from the current one, i.e. the standard matrix substraction. This modifies the current matrix and does not return a new instance.

### times
Returns the result of multiplying the current matrix with another one. Note that the supplied matrix has to be transformation Matrix.

### apply
Applies the current transformation to the given 2D-point, thus returning the transformed point.

### toString
Returns a string representation in a form which can be used in SVG, i.e. "matrix(...)".

## Node

A node or vertex can be a stand-alone object or part of a Graph structure. You can instantiate a Node as follows:

    var node = kendo.diagram.Node();

or with a specific identifier as

    var node = kendo.diagram.Node("myId");

A Node has three collections defined which hold the incidence structure of a Graph but which can be also used outside the Graph:

 * the **links** array holds all the links attached to the Node
 * the **outgoing** array holds all the links starting at the Node (i.e. the Node is always the **source** of these links)
 * the **incoming** array holds all the links ending at the Node (i.e. the Node is always the **target** of these links)

You normally only use these array to inspect their content but use the appropriate methods of the Node, the Link or Graph object which automatically manage these collections.
For example, the creation of a new link

    var link = new kendo.diagram.Link(a,b);

will automatically add this link to the outgoing collection of the 'a' node and to the incoming collection of the 'b' node.

### isIsolated
Returns whether this node has no links attached and thus disconnected from other nodes.

### is LinkedTo
Returns whether there is at least one link with the given (complementary) node. This can be either an incoming or outgoing link.

### getChildren
Gets the children of this node, defined as the adjacent nodes with a link from this node to the adjacent one.

###getParents
Gets the parents of this node, defined as the adjacent nodes with a link from the adjacent node to this one.

### clone
Returns a clone of the Node. Note that the identifier is not cloned since it's a different Node instance.

### adjacentTo
Returns whether there is a link from the current node to the given node.

### removeLink
Removes the given link from the link collection this node owns.

### hasLinkTo
Returns whether there is a (outgoing) link from the current node to the given one.

### degree
Returns the degree of this node, i.e. the sum of incoming and outgoing links.

### incidentWith
Returns whether this node is either the source or the target of the given link.

### getLinksWith
Returns the links between this node and the given one.

### getNeighbors
Returns the nodes (either parent or child) which are linked to the current one.

##Link

A link is always directed and is defined by its **source** (aka origin, 'from' endpoint, start vertex or start node) and **target** (aka sink, 'to' endpoint, end vertex or end node);

    var from = new Node("from");
    var to = new Node("to");
    var link = new Link(from, to);

### getComplement

Return the opposite node in the link of the given node or null if the given node is not part of the link

    var from = new Node("from");
    var to = new Node("to");
    var link = new Link(from, to);
    var opposite = link.getComplement(from); // returns the "to" node
    var nothing = link.getComplement(new Node()) // returns null

### getCommonNode

Returns the overlap (i.e. overlapping node) of the current link with the given one, or null if none.

### isBridging

Returns whether the current link is bridging the given nodes, i.e. whether the given nodes correspond to the source and target of the current link.

    var from = new Node("from");
    var to = new Node("to");
    var link = new Link(from, to);
    var isBridging = link.isBriding(from, to); // returns true

### getNodes
Returns the source and target of this link as a tuple (array of two elements).

    var from = new Node("from");
    var to = new Node("to");
    var link = new Link(from, to);
    var tuple = link.getNodes(); // returns [from, to]

### incidentWith

Returns whether the given node is either the source or the target of the current link.

### adjacentTo

 Returns whether the given link is a continuation of the current one. This can be both via an incoming or outgoing link.

### changeSource

Changes the source-node of the link. It preserves the identifier of the link but effectively changes the incidence structure; incoming and other collections are internally changed through this method.

### changeTarget

Similar to the changeSource method, it changes the target-node of the link.

### changeNodes

A combination of the changeSource and changeTarget methods; it replaces the source and target nodes of the current link.

### reverse

Reverses the direction of the (directed) link, thus inverting the roles of source and target nodes.

### clone

Returns a clone of the current link which consists of the same instance of the source and target node but different properties (identifier, weight and so on).

### createReverseEdge

Returns a clone of the current link with the reversed direction.

## Graph

The graph structure implements the classic mathematical object comprised of nodes and links. Nodes are uniquely identified inside the graph by means of their identifier (id). Links are
 in essence just 2-tuples of nodes.
You can define graphs explicitly by means of the API methods or via the so-called linearized form (which is a serialization of the graph containing only the essential adjacency structure).

Using the API you can build up a graph as follows:

     var g = new diagram.Graph("G1"); // specifying an identifier 'G1'
     var h = new diagram.Graph(); // auto-assigned identifier

     var n1 = g.addNode("n1"); // a new node with identifier "n1"
     var n2 = g.addNode(); // node with auto-identifier

     var link = g.addLink("n1", n2); // you can use identifiers or objects to specify the source and target of a link

Using the linearized version of a graph you could more easily define the previous graph as:

     var g = kendo.diagram.Graph.parse(["1->2"]);

Conversely, you can linearize an existing graph:

     var shortForm = g.linearize();

There are various options when using these methods, see below for more details.

The relational (often called 'adjacency') structure of the graph is internally not defined by means of linked lists or an adjacency matrix, rather each node defines three collections

- the **incoming links**: links with the target equal to the node
- the **outgoing links**: links with the source equal to the node
- all the **links**: all links attached to the node

which overdefines the topology of the graph but alleviates the development of algorithms. In most circumstances you don't access or update these collections but rather make use of the appropriate methods (add, remove...) which internally maintain these link collections.

#Predefined and random graphs

Besides the linearized format which makes it easy to create diagrams the framework also defines a few predefined graphs and some methods generating random diagrams.

The predefined graphs are:

- **Mindmap**: a typical mindmap diagram.
- **EightGraph**: a graph with some cycles.
- **ThreeGraph**: a simple graph with three nodes
- **Workflow**: a typical workflow diagram (with cycles)

There is a simple method which turns a Graph into a diagram as follows:

    // assuming 'diagram' is the name of the Kendo diagram control instance
    var graph = kendo.diagram.Graph.Predefined.Mindmap();
    kendo.diagram.Graph.Utils.createDiagramFromGraph(diagram, graph);

The **createDiagramFromGraph** method also has an optional final boolean parameter which turns layout on or off. If you specify

    kendo.diagram.Graph.Utils.createDiagramFromGraph(diagram, graph, true);

the force-directed layout will be applied after the diagram has been generated.

To generate random diagram you can use the randomDiagram method directly on the control instance

     diagram.randomDiagram(50, 3, true);

which will generate a random tree diagram with 50 nodes, a maximum incidence (i.e. degree) of three. The last parameter specified whether the random diagram should be a tree. If set to false it means there are potentially cycles.
You can also use the following methods from the utilities:

- **createBalancedTree**: creates a balanced tree (all nodes have the same degree)
- **createBalancedForest**: creates a forest of balanced trees
- **createRandomConnectedGraph**: creates a connected graph (optionally a tree).

These methods are aliased in the Predefined class too, so you can create a balanced forest like so

    var g = kendo.diagram.Graph.Predefined.Forest(3, 2, 3); // 3 levels, degree two, three trees
    var useRandomSizes = true; // create nodes or shapes with random width and height
    kendo.diagram.Graph.Utils.createDiagramFromGraph(diagram, g, false, useRandomSizes);

