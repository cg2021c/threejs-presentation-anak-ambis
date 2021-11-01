# Geometry grouping and merging
## Grouping objects together
In Three.js we can group objects when working with multiple materials. When we create a mesh from a geometry using multiple materials, Three.js creates a group.
In this case, Grouping sphere and cube
<!-- <img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/image/picture1.jpg?raw=true"> -->
The following code shows how to do this:
```bash
sphere = createMesh(new THREE.SphereGeometry(5, 10, 10));
cube = createMesh(new THREE.BoxGeometry(6, 6, 6));
group = new THREE.Group();
group.add(sphere);
group.add(cube);
scene.add(group);
```
The full source code in [here](https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/01-grouping.html)

Creating groups is very easy. Every mesh we create can contain child elements, which can be added using the add function. The effect of adding a child object to a group is that we can move, scale, and rotate the parent object, and all the child objects will also be affected.
| Action | Result 
| :---: | :---: 
| move | ![screen-gif](https://media.giphy.com/media/k5PO2tWz5d8mw6d7on/giphy.gif)
| :---: | :---: 
| scale | ![screen-gif](https://media.giphy.com/media/Pkg8NKirneAbjfKksg/giphy.gif)
| :---: | :---: 
| rotate | ![screen-gif](https://media.giphy.com/media/70EDp6aHFIP24sSZhF/giphy.gif)

Scale and position are very easy. One thing to keep in mind, though, is that when we rotate a group, it doesn't rotate the objects inside it separately; it rotates the entire group around its own center.In this example, we placed an arrow using the THREE.ArrowHelper object at the center of the group to indicate the rotation point:

```bash
var arrow = new THREE.ArrowHelper(new THREE.Vector3(0, 1, 0),
group.position, 10, 0x0000ff);
scene.add(arrow);
```

![screen-gif](https://media.giphy.com/media/t0wJi4NIbG5SkPQiii/giphy.gif)

When using a group, we can still refer to, modify, and position the individual geometries.The only thing you need to remember is that all positions, rotations, and translations are done relative to the parent object.<br>
![screen-gif](https://media.giphy.com/media/kjQJzgdeNtr57gMhiq/giphy.gif)
<br>
<br>
<br>
<br>
## Merging multiple meshes into a single mesh
When we're dealing with a very large number of objects. however, performance will become an issue. With groups, we're still working with individual objects that each
need to be handled and rendered separately. With using THREE.Geometry.merge(), we can merge geometries together and create a combined one.<br>

If we open the [02-merging.html](https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-08/02-merging.html) example, we can see a scene with a set of randomly distributed semitransparent cubes.<br>
<!-- <img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/image/picture3.jpg?raw=true"> -->
The problem is performance degradation as the number of cubes increases. In our case, this happens at around 10,839 objects, where the refresh rate drops to around 8 Frames Per Second (fps) instead of the normal 60 fps,With THREE.Geometry.merge(), we can solve this problem.<br>
To do this, we use the following few lines of code:
```bash
var geometry = new THREE.Geometry();
for (var i = 0; i < controls.numberOfObjects; i++) {
var cubeMesh = addcube();
cubeMesh.updateMatrix();
geometry.merge(cubeMesh.geometry,cubeMesh.matrix);
}
scene.add(new THREE.Mesh(geometry, cubeMaterial));
```
The full source code in [here](https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/02-merging.html)
| Action | Result 
| :---: | :---: 
| Before using THREE.Geometry.merge() | <img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/raw/main/Geometry%20Grouping%20and%20Merging/image/picture3.jpg?raw=true">
| :---: | :---: 
| After using THREE.Geometry.merge() | <img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/raw/main/Geometry%20Grouping%20and%20Merging/image/picture4.jpg?raw=true">
