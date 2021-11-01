# Geometry grouping and merging
## Grouping objects together
In Three.js we can group objects when working with multiple materials. When we create a mesh from a geometry using multiple materials, Three.js creates a group.
In this case, Grouping sphere and cube
<img src="https://github.com/cg2021c/threejs-presentation-anak-ambis/blob/main/Geometry%20Grouping%20and%20Merging/image/picture1.jpg?raw=true">
The following code shows how to do this:
```bash
sphere = createMesh(new THREE.SphereGeometry(5, 10, 10));
cube = createMesh(new THREE.BoxGeometry(6, 6, 6));
group = new THREE.Group();
group.add(sphere);
group.add(cube);
scene.add(group);
```

Creating groups is very easy. Every mesh you create can contain child elements, which can be added using the add function. The effect of adding a child object to a group is that we
can move, scale, and rotate the parent object, and all the child objects will also be affected.
| Action | Result 
| :---: | :---: 
| move | ![screen-gif](https://media.giphy.com/media/hKk9tCVkhF33BZAbZ2/giphy.gif)
| :---: | :---: 
| scale | ![screen-gif](https://media.giphy.com/media/hKk9tCVkhF33BZAbZ2/giphy.gif)
| :---: | :---: 
| rotate | ![screen-gif](https://media.giphy.com/media/hKk9tCVkhF33BZAbZ2/giphy.gif)
