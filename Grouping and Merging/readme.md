# Geometry grouping and merging
## Grouping objects together
In Three.js we can group objects when working with multiple materials. When we create a mesh from a geometry using multiple materials, Three.js creates a group.
In this case, Grouping sphere and cube
<img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/image/picture1.jpg?raw=true">
The following code shows how to do this:
```bash
sphere = createMesh(new THREE.SphereGeometry(5, 10, 10));
cube = createMesh(new THREE.BoxGeometry(6, 6, 6));
group = new THREE.Group();
group.add(sphere);
group.add(cube);
scene.add(group);
```

Creating groups is very easy. Every mesh you create can contain child elements, which can be added using the add function. The effect of adding a child object to a group is that we can move, scale, and rotate the parent object, and all the child objects will also be affected.
| Action | Result 
| :---: | :---: 
| move | ![screen-gif](https://media.giphy.com/media/k5PO2tWz5d8mw6d7on/giphy.gif)
| :---: | :---: 
| scale | ![screen-gif](https://media.giphy.com/media/Pkg8NKirneAbjfKksg/giphy.gif)
| :---: | :---: 
| rotate | ![screen-gif](https://media.giphy.com/media/70EDp6aHFIP24sSZhF/giphy.gif)

Scale and position are very straightforward. One thing to keep in mind, though, is that when we rotate a group, it doesn't rotate the objects inside it separately; it rotates the entire group around its own center.In this example, we placed an arrow using the THREE.ArrowHelper object at the center of the group to indicate the rotation point:

```bash
var arrow = new THREE.ArrowHelper(new THREE.Vector3(0, 1, 0),
group.position, 10, 0x0000ff);
scene.add(arrow);
```
<img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Grouping%20and%20Merging/image/picture2.jpg?raw=true">
