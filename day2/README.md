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