# Loading models from other supported formats
We're going to quickly skim over these file formats as they all follow the same principles:
1. Include ```[NameOfFormat]Loader.js``` in web page. 
2. Use ```[NameOfFormat]Loader.load()``` to load a URL. 
3. Check what the response format for the callback looks like and render the result. 

## STL
Usage
1. Include ```<script type="text/javascript" src="../libs/STLLoader.js"></script>```
2. Then load models 
```js
var loader = new THREE.STLLoader();
var group = new THREE.Object3D();
loader.load("../assets/models/SolidHead_2_lowPoly_42k.stl", function (geometry) {
  var mat = new THREE.MeshLambertMaterial({color: 0x7777ff});
  group = new THREE.Mesh(geometry, mat);
  group.rotation.x = -0.5 * Math.PI;
  group.scale.set(0.6, 0.6, 0.6);
  scene.add(group);
});
```
3. Result [09-load-stl.html](https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-08/09-load-stl.html)

From the source code for these examples, we might see that for some of them, we need to change some material
properties or do some scaling before the model is rendered correctly. The reason we need to do this is because of the 
way the model is created in its external application, giving it different dimensions and grouping than we normally use in 
Three.js.

## BABYLON
The Babylon loader is slightly different from the other loaders. With this loader, we don't load a single THREE.Mesh or THREE.Geometry instance, but with this 
loader, we load a complete scene, including lights.
Usage
1. Include ```<script type="text/javascript" src="../libs/BabylonLoader.js"></script>```
2. Then load models 
```js
var loader = new THREE.BabylonLoader();
var group = new THREE.Object3D();
loader.load("../assets/models/babylon/skull.babylon", function (loadedScene) {
  console.log(loadedScene.children[1].material = new THREE.MeshLambertMaterial());
  scene = loadedScene;
});
```
3. Result [17-load-babylon.html](https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-08/17-load-babylon.html)

# Show proteins from Protein Data Bank

Protein Data Bank (www.rcsb.org) contains detailed information about many different molecules and proteins. Besides the 
explanation of these proteins, they also provide a way to download the structure of these molecules in the PDB format. 
Three.js provides a loader for files specified in the PDB format. We will try how we can parse PDB files and visualize them with Three.js.

The first thing we always need to do to load in a new file format is include the correct loader in Three.js, as follows:

```<script type="text/javascript" src="../libs/PDBLoader.js"></script>```

Loading a PDB file is done in the same manner as the previous formats, as follows: 

```js
var loader = new THREE.PDBLoader(); 
var group = new THREE.Object3D(); 
loader.load("../assets/models/diamond.pdb", function (geometry, geometryBonds) { 
  var i = 0; 
 
  geometry.vertices.forEach(function (position) { 
    var sphere = new THREE.SphereGeometry(0.2); 
    var material = new THREE.MeshPhongMaterial({color: geometry.colors[i++]}); 
    var mesh = new THREE.Mesh(sphere, material); 
    mesh.position.copy(position); 
    group.add(mesh); 
  }); 
 
  for (var j = 0; j < geometryBonds.vertices.length; j += 2) { 
    var path = new THREE.SplineCurve3([geometryBonds.vertices[j], geometryBonds.vertices[j + 1]]); 
    var tube = new THREE.TubeGeometry(path, 1, 0.04) 
    var material = new THREE.MeshPhongMaterial({color: 0xcccccc}); 
    var mesh = new THREE.Mesh(tube, material); 
    group.add(mesh); 
  } 
  console.log(geometry); 
  console.log(geometryBonds); 
 
  scene.add(group); 
});
```

In this example, THREE.PDBLoader pass in the model file we want to load, and provide a 
callback that is called when the model is loaded. For this specific loader, the callback function is called with two 
arguments: geometry and geometryBonds. The vertices from the geometry argument supplied contain the positions of the 
individual atoms, and geometryBounds is used for the connections between the atoms. 
For each vertex, we create a sphere with the color that is also supplied by the model:

```js
  var sphere = new THREE.SphereGeometry(0.2);
  var material = new THREE.MeshPhongMaterial({color: geometry.colors[i++]});
  var mesh = new THREE.Mesh(sphere, material);
  mesh.position.copy(position);
  group.add(mesh);
```

Each connection is defined like this:

```js
var path = new THREE.SplineCurve3([geometryBonds.vertices[j], geometryBonds.vertices[j + 1]]); 
var tube = new THREE.TubeGeometry(path, 1, 0.04) 
var material = new THREE.MeshPhongMaterial({color: 0xcccccc}); 
var mesh = new THREE.Mesh(tube, material); 
group.add(mesh);
```
For the connection, we must create a 3D path using the THREE.SplineCurve3 object. This path is used as input 
for THREE.Tube and used to create the connection between the atoms. All the connections and atoms are added to a group, 
and this group is added to the scene.
