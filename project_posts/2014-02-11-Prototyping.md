# Prototyping
Began prototyping in WebGL with Three.js. I'm using an orthographic camera to keep things 2D.

## Circles
![Circles](../project_images/prototype_dashedline.png?raw=true "Circles")
I put together a simple helper method for generating circles and dashed circles in WebGL.

```
function circle(r, segments, stroke, dashed) {
   	var radius = r,
   	    geometry = new THREE.Geometry(),
        material;

	for (var i = 0; i <= segments; i++) {
   		var theta = (i / segments) * Math.PI * 2,
   			  vector = new THREE.Vector3(Math.cos(theta) * radius, Math.sin(theta) * radius, 0);

  		geometry.vertices.push(vector);
	}

    if (dashed !== true) {
    	material = new THREE.LineBasicMaterial({color: 0xFFFFFF, linewidth: stroke});
    	line = new THREE.Line(geometry, material);
    } else {
    	material = new THREE.LineDashedMaterial({color: 0xFFFFFF, linewidth: stroke});
    	line = new THREE.Line(geometry, material, THREE.LinePieces);
    }

	return line;
}
```
## WebCam Mask
I utilized getUserMedia to access the webCam and then used that to texture a Quad. In order to create a circular mask I first draw the video to a 2D canvas and then clip the video, then use the rendered result as the final texture on the Quad.

![Video Mask](../project_images/prototype_video_mask.png?raw=true "Video Mask")

## Research
Also did some quick looking into GLSL Fragment Shader examples:
http://glsl.heroku.com/e#13905.0
http://glsl.heroku.com/e#13789.0
http://glsl.heroku.com/e#13744.0
http://glsl.heroku.com/e#13475.0
http://glsl.heroku.com/e#13427.0