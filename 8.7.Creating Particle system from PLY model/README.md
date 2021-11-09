# Creating Particle system from PLY model
PLY is a computer file format known as the Polygon File Format or the Stanford Triangle Format. It was principally designed to store three-dimensional data from 3D scanners.

Working with the PLY format isn't that much different from the other formats. You include the loader, provide a callback,
and visualize the model. For this example, however, we're going to do something different. Instead of rendering the 
model as a mesh, we'll use the information from this model to create a particle system. The following screenshot shows this example:

![image](https://user-images.githubusercontent.com/73778173/139693299-aab083c6-ad8e-49f1-9865-d13072ff1b8c.png)

The JavaScript code to render the preceding screenshot, as follows:
```
var loader = new THREE.PLYLoader();
var group = new THREE.Object3D();
loader.load("../assets/models/test.ply", function (geometry) {
var material = new THREE.PointCloudMaterial({

color: 0xffffff,
size: 0.4,
opacity: 0.6,
transparent: true,
blending: THREE.AdditiveBlending,
map: generateSprite()
});
group = new THREE.PointCloud(geometry, material);
group.sortParticles = true;
scene.add(group);
});
```
As you can see, we use THREE.PLYLoader to load the model. The callback returns geometry, and we use this geometry as
input for THREE.PointCloud. As you can see, with Three.js, it is very easy to combine models from various sources and render them in
different ways, all with a few lines of code.
