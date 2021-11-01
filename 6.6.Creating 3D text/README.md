# Creating 3D text

In the next part of this chapter, we'll have a quick look at how you can create 3D text effects. First, we'll look at how to render text using the fonts provided by Three.js, and after that, we'll have a quick look at how you can use your own fonts for this. Rendering text Rendering text in Three.js is very easy. All you have to do is define the font you want to use and use the same extrude properties we saw when we discussed THREE.ExtrudeGeometry. The following screenshot shows the 07-textgeometry.html example of how to render text in Three.js:

<a href="../learning-threejs-master/chapter-06/07-text-geometry.html">
  <img src="../img/5.7.png">
</a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/07-text-geometry.html"><h3>Try Yourself</h3></a>

The code required to create this 3D text is as follows:

```js
var loadedFont;
var fontload = new THREE.FontLoader();
fontload.load(
  "../../assets/fonts/bitstream_vera_sans_mono_roman.typeface.json",
  function (response) {
    loadedFont = response;
    render();
  }
);
var options = {
  size: 90,
  height: 90,
  font: loadedFont,
  bevelThickness: 2,
  bevelSize: 4,
  bevelSegments: 3,
  bevelEnabled: true,
  curveSegments: 12,
  steps: 1,
};
// the createMesh is the same function we saw earlier
text = createMesh(new THREE.TextGeometry("Learning Three.js", options));
scene.add(text);
```

In this code fragment, you can see that we first have to load the font. For this, Three.js provides THREE.FontLoader(), where we provide the name of the font to load, and once loaded, Three.js will use the callback with the loaded font (response). In this example, we just assign it to a variable, and call the render function. The font that we loaded is also assigned to the options object we use in the constructor of the THREE.TextGeometry. The options we can pass into THREE.TextGeometry match those that we can pass in THREE.ExtrudeGeometry, plus a couple of ones specifically for THREE.TextGeometry

Let's look at all the options we can specify for THREE.TextGeometry:

| Parameter      | Mandatory | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| -------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| size           | No        | This is the size of the text. The default value is 100.                                                                                                                                                                                                                                                                                                                                                                                                 |
| height         | No        | This is the length (depth) of the extrusion. The default value is 50.                                                                                                                                                                                                                                                                                                                                                                                   |
| font           | Yes       | The loaded font to use for the text.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| bevelThickness | No        | This is the depth of the bevel. The bevel is the rounded corner between the front and back faces and the extrusion. The default value is 10.                                                                                                                                                                                                                                                                                                            |
| bevelSize      | No        | This is the height of the bevel. The default value is 8.                                                                                                                                                                                                                                                                                                                                                                                                |
| bevelSegments  | No        | This defines the number of segments that will be used by the bevel. The more segments there are, the smoother the bevel will look. The default value is 3.                                                                                                                                                                                                                                                                                              |
| bevelEnabled   | No        | If this is set to true, a bevel is added. The default value is false                                                                                                                                                                                                                                                                                                                                                                                    |
| curveSegments  | No        | This defines the number of segments used when extruding the curves of shapes. The more segments there are, the smoother the curves will look. The default value is 4.                                                                                                                                                                                                                                                                                   |
| steps          | No        | This defines the number of segments the extrusion will be divided into. The default value is 1.                                                                                                                                                                                                                                                                                                                                                         |
| extrudePath    | No        | This is the path along which the shape should be extruded. If this isn't specified, the shape is extruded along the z axis.                                                                                                                                                                                                                                                                                                                             |
| uvGenerator    | No        | When you use a texture with your material, the UV mapping determines what part of a texture is used for a specific face. With the UVGenerator property, you can pass in your own object that will create the UV settings for the faces that are created for the passed-in shapes. More information on UV settings can be found in Chapter 10, Loading and Working with Textures. If none are specified, THREE.ExtrudeGeometry.WorldUVGenerator is used. |

# Adding custom fonts

There are a couple of fonts provided by Three.js that you can use in your scenes. These fonts are based on the fonts provided by the TypeFace.js library. TypeFace.js is a library that can convert TrueType and OpenType fonts to JavaScript. The resulting JavaScript file or JSON file can be included in your page, and the font can then be used in Three.js. In older versions, the JavaScript file was used, but in later Three.js versions, Three.js switched to using the JSON file.

To convert an existing OpenType or TrueType font, you can use the web page
at http://gero3.github.io/facetype.js
