# Saving and loading in Three.js JSON format
We can use Three.js' JSON format for two different scenarios in Three.js. We can use it to save and load a <br>
single `THREE.Mesh`, or we can use it to save and load a complete scene.

## Saving and loading THREE.Mesh
To demonstrate saving and loading, we used a simple example based on **THREE.TorusKnotGeometry**. With this example, <br>
we can create a **torus knot** and using the save button from the Save & Load menu, we can save the current geometry. For this example, we save using the HTML5 local storage API. This API allows us to easily store persistent information in the client's browser and retrieve it at a later time. <br>

The following shows this example: <br>
![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/75240358/139702862-f9d5ebca-a397-41c4-a523-70959b275fac.gif)  
The only thing we need to do to export `THREE.Mesh` as JSON is the following: 
```js
var result = knot.toJSON();
localStorage.setItem("json", JSON.stringify(result));
```
This results in a JSON string :
```js
{
    "metadata": {   
        "version": 4.3,
        "type": "Object",
        "generator": "ObjectExporter"
    },  
    "geometries": [{
        "uuid": "53E1B290-3EF3-4574-BD68-E65DFC618BA7",
        "type": "TorusKnotGeometry",
        "radius": 10,
        "tube": 1,
        "radialSegments": 64,
        "tubularSegments": 8,
        "p": 2,
        "q": 3,
        "heightScale": 1
    }],
...
}
```
Three.js saves all the information about `THREE.Mesh`. To save this information using the HTML5 local storage API, all <br>
we have to do is call the `localStorage.setItem` function. The first argument is the key value (json) that we can later <br>
use to retrieve the information we passed in as the second argument. <br><br>
Loading `THREE.Mesh` back into Three.js:
```js
var json = localStorage.getItem("json");

if (json) {
    var loadedGeometry = JSON.parse(json);
    var loader = new THREE.ObjectLoader();
    loadedMesh = loader.parse(loadedGeometry);
    loadedMesh.position.x -= 50;
    scene.add(loadedMesh);
}
```
- Use the `localStorage.getItem` function provided by the HTML5 local storage API.
- Three.js provides a helper object called `THREE.ObjectLoader`, which we can use to convert JSON to `THREE.Mesh`.
- The loader also provides a `load` function, where we can pass in the URL to a file containing the JSON definition.  

We only saved `THREE.Mesh`. Use `THREE.SceneExporter` to save the complete scene, including the lights and the cameras. 
