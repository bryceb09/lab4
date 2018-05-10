# 3D Force Graph
Spring 2018 | Geography 4/572 | Geovisualization: Geovisual Analytics 

**Attribution:** [Vasco Asturiano](https://github.com/vasturiano)

The force graph is created using D3 which is a JavaScript library used for visualizing data with HTML, SVG, and CSV. The graph will be comprised of nodes and links connecting informaiton to form a graph that will have the ability to allow users to maipulate the graph through pulling the nodes, roatating the graph (since it has a 3D aspect), and mouse over to view the data that each node represents. 

## 1. Set up the workspace

In your IDE (Webstorm), open a blank `HTML` document to prepare for editing.

We will begin by adding the `d3.js` file to your blank `HTML` by adding it inside the `head` tag.

```JavaScript
<script src="https://unpkg.com/3d-force-graph@1.31.4/dist/3d-force-graph.js"></script>
```

## 1.1 Adding Style Tag

As of now you have added the `d3.js` file to your blank `HTML` file. Now we will add the `style` tage to your document which will be placed in the `head` along with the `d3.js`. Once you have done that your `HTML` file should look like this.

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Force Graph</title>
    <style> body { margin: 0; } </style>
    <script src="https://unpkg.com/3d-force-graph@1.31.4/dist/3d-force-graph.js"></script>
</head>
<body>

</body>
</html>
```
## 2. Building the Graph

Now that you have set the `style` and added the `d3.js` tile to your `HTML` file you will begin to build your graph. To do so begin by creating a `div` element which is a container for the `id` __3d-graph__ and you will add the `div` element indside the `body`.

```HTML
<div id="3d-graph"></div>
```

## 2.1 Adding the Script


From this point you will begin to add the `JavaScript` into your `HTML` file by adding the script below the `div` element while still being contained within the `body`. To add the `JavaScript` to your document it need to be added whithin the tag `script` while still be completely inside the `body`.

The first line of the `scrpit` is `const Graph = ForceGraph3D()` this means you are creating a read-only reference to a value in this case the value of the `const graph` is `ForceGraph3D()`. The next line of code is ` (document.getElementById('3d-graph'))` this refers to the ability for your graph to return the element that has the `ID` attribute with the specified value in this case it's `3d-graph`. From here the graph is broken down into ` .jsonUrl`, `.nodeLabel`, `.nodeAutoColorBy`, `.linkDirectionalParticles`, and `.linkDirectionalParticleSpeed(d => d.value * 0.001);`.

`.jsonUrl` is the URL of the json file that you will load the graph data directly from. `.nodeLabel` is the node object accessor function that will display the name when you mouse over the node. `.nodeAutoColorBy` is a node object accessor function to automatically group colors and pick a random color for each group displayed. `.linkDirectionalParticles` is a link object accessor function to display the number of particles over the link line and can be used to indicate link directionality. In your graph this is displayed by the lines connecting the nodes together based on attribue or numerical constant of particals. `.linkDirectionalParticleSpeed(d => d.value * 0.001);` is the link object accessor function for the directional particals speed. For your graph this is the speed at which you can drag and move the nodes in your case the speed will be .001. Having reviewed all the parts that make of the `script` you are now ready to add the `JavaScript` to your `HTML` file.

```JavaScript
 const Graph = ForceGraph3D()
    (document.getElementById('3d-graph'))
        .jsonUrl('../datasets/miserables.json')
        .nodeLabel('id')
        .nodeAutoColorBy('group')
        .linkDirectionalParticles("value")
        .linkDirectionalParticleSpeed(d => d.value * 0.001);
```






