#README DAY 2
##stuff about assets
For the second day, I did a close reading of Aframe's "Hello World" tutorial,
and adding in Knight Lab assets. I spent some time reading about Aframe's Asset Management
System which puts all your assets in one place and preloads them for better performance. All of Aframe's entities have behavior which prevents them from rendering before all of these assets are
fetched. Audio and video assets wil only block a sign if they're set to autoplay.

If some of your assets are loading slowly, you can set a timeout which will allow the scene to load regardless of whether all the assets are present. This timeout is passed as an attribute to a-assets.

When all assets have finished loading, <a-assets> will emit a *loaded* event

All A-Frame elements inherit from the AFRAME.ANode prototype. ANode controls how elements load and initialize. Nodes load from the bottom up and an Node can't initialize until all of its child nodes have loaded. Since <a-assets> is a child of <a-scene> the scene won't load until all the assets have.

<a-asset-item> is used for miscellaneous assets that aren't images, sounds, images or videos--most often it will be a 3D model. <a-asset-item> calls out to the THREE.XHRLoader.

##Stuff about interaction
<a-scene> has a default camera, but if we want to add a cursor, we have to explicitly define a camera, so we can make the cursor a child of that camera.

##Day 3
Today I took a look at the light component. Lights apply to all materials unless we've applied `shader: flat` to them. Lights are pretty tough on performance so its good to keep them to a minimum.

By default, A-Frame provides us with a default ambient and directional light, these are removed whenever we specify a light within the scene.

The light component has three properties type, color and intensity.

The type attribute has four potential values. The default value is directional. A directional light is in a given direction, but infinitely far away, so absolute position does not effect a directional light's intensity. You can use the postion attribute of the directional light to give it a direction but only the angle set by the position actually matters.

A hemisphere light is like an ambient light, but it allows you to pass in a groudColor attribute so you can have distinct colors of light coming from different parts of the scene (for like ground and sky for example).

Point lights are "lightbulb" type lights. They are omnidirectional and the intensity of the light they give off is dependent on their distance from the object they're lighting. You can pass in a distance attibute to set the point where the intensity of the light becomes zerro. You can also set the rate at which the light dims along its distance by setting a decay attribute.

Spot lights are spotlights. Their light is in one direction and varies in intensity based on position. Spotlights can take an angle, a rate of decay, a distance to zero, a penumbra in the form of a percent, and a target. If you want your spotlight to be fixed on one element, you can pass it's id to the target attribute, but if you want to transform your spotlight by varying the Z axis of its position, you should set it to null.