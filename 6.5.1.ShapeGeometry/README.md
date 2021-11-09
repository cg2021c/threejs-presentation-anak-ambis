# ShapeGeometry

Extruding from SVG When we discussed THREE.ShapeGeometry, we mentioned that SVG follows pretty much the same approach of drawing shapes. SVG very closely matches how Three.js handles shapes. In this section, we'll look at how we can use a small library from https://github.com/asutherland/d3-threeD to convert SVG paths to a Three.js shape (Three.js also provides a specific THREE.SVGLoader, which is explained in Chapter 8, Creating and Loading Advanced Meshes and Geometries). For the 05-extrudesvg.html example, we've taken an SVG drawing of the Batman logo and used ExtrudeGeometry to convert it to 3D, as shown in the following screenshot:

<a href="../learning-threejs-master/chapter-06/05-extrude-svg.html">
  <img src="../img/5.5.png">
</a>

<a href="../learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>CODE</h3></a>

<a href="../learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>CODE</h3></a>

<a href="../learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>CODE</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>Try Yourself</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>Try Yourself</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/05-extrude-svg.html"><h3>Try Yourself</h3></a>

The following code fragment shows how we can load in the SVG we saw earlier, convert it to THREE.ExtrudeGeometry, and show it on screen:

```js
function drawShape() {
  var svgString = document.querySelector("#batman-path").getAttribute("d");
  var shape = transformSVGPathExposed(svgString);
  return shape;
}
var options = {
  amount: 10,
  bevelThickness: 2,
  bevelSize: 1,
  bevelSegments: 3,
  bevelEnabled: true,
  curveSegments: 12,
  steps: 1,
};
shape = createMesh(new THREE.ExtrudeGeometry(drawShape(), options));
```

In this code fragment, we'll see a call to the transformSVGPathExposed function. This function is provided by the d3-threeD library and takes an SVG string as an argument. We get this SVG string directly from the SVG element with the following expression: document.querySelector("#batman-path").getAttribute("d"). In SVG, the d attribute contains the path statements used to draw a shape. Add a nice-looking shiny material and a spotlight and we've recreated this example.

## ShapeGeometry
Creates an one-sided polygonal geometry from one or more path shapes.

### Code Example

```js
const x = 0, y = 0;

const heartShape = new THREE.Shape();

heartShape.moveTo( x + 5, y + 5 );
heartShape.bezierCurveTo( x + 5, y + 5, x + 4, y, x, y );
heartShape.bezierCurveTo( x - 6, y, x - 6, y + 7,x - 6, y + 7 );
heartShape.bezierCurveTo( x - 6, y + 11, x - 3, y + 15.4, x + 5, y + 19 );
heartShape.bezierCurveTo( x + 12, y + 15.4, x + 16, y + 11, x + 16, y + 7 );
heartShape.bezierCurveTo( x + 16, y + 7, x + 16, y, x + 10, y );
heartShape.bezierCurveTo( x + 7, y, x + 5, y + 5, x + 5, y + 5 );

const geometry = new THREE.ShapeGeometry( heartShape );
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
const mesh = new THREE.Mesh( geometry, material ) ;
scene.add( mesh );
```

### Constructor

ShapeGeometry(shapes : Array, curveSegments : Integer)

shapes — Array of shapes or a single shape. Default is a single triangle shape.

curveSegments - Integer - Number of segments per shape. Default is 12.

### Properties

See the base <a href="https://threejs.org/docs/index.html?q=lathe#api/en/core/BufferGeometry">BufferGeometry</a> class for common properties.

.parameters : Object

An object with a property for each of the constructor parameters. Any modification after instantiation does not change the geometry.

### Methods

See the base <a href="https://threejs.org/docs/index.html?q=lathe#api/en/core/BufferGeometry">BufferGeometry</a> class for common methods.

### Source

<a href="https://github.com/mrdoob/three.js/blob/master/src/geometries/ShapeGeometry.js">src/geometries/ShapeGeometry.js</a>

