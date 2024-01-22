# Material & Rendering

# Rendering:

Our rendering style is somewhat like [cel shading](https://en.wikipedia.org/wiki/Cel_shading).  We don’t use gradients or soft transitions.  We describe form with simplified plane changes.  

![celshadeline.png](https://cdn-production.joinhighrise.com/create-portal/celshadeline_9b710e628a.png)

For a breakdown of drawing in the Highrise style check out our Drawing & Designing guide!


## **Shading/Shadow Tones**

Generally you want to increase around 5~10 digits saturation with 10~15 digits brightness. 

This helps an item stay bright and saturated without it getting muddy.

![shadowtone1.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone1_916a20f344.png)

Generally, we make our shadows more saturated but don’t change the hue. However, sometimes a little hue shifting can add nice dimension to the item.

![shadowtone2.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone2_f4d800ea03.png)

However, this can lead to issues. The items sometimes looks like it’s under a different light effect or has a filter on it, which looks really cool in photography or concept art, but not in our game where we want to have consistent lighting.

![shadowtone3.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone3_d8c68e45d5.png)

![shadowtone4.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone4_7eb87f4725.png)


Another issue is that when we do this, often the hues we shift to don’t match.  It’s particularly obvious on white items.  

![shadowtone5.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone5_4d13cd49b5.png)

So it’s best to use hue shifting very minimally, if at all.  

![shadowtone6.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone6_e539b5910a.png)

Exceptions are particular materials, like iridescent/holo material, gemstones, neon, gold.  

Another exception is the use of the color yellow. Yellow can be a very tricky to shade because dark yellow tends to get kind of muddy/brown. Good practice is shifting the darker tones to yellow colors to be more orange.

![shadowtone7.png](https://cdn-production.joinhighrise.com/create-portal/shadowtone7_fef22ca532.png)


## Rendering a Shiny Object

In general, we don’t want to over render an object. Over-rendering can leave an item looking like a fake 3D rendering, which doesn't suit our game style. The basic idea is to capture the base color, a layer of shading, then add the darkest shading or brightest highlight if needed (but this is usually subtle). Ideally, a general textured object (like a cotton t-shirt or skin) would only have two to three tones of shading.

![shinyrender1.png](https://cdn-production.joinhighrise.com/create-portal/shinyrender1_c16d3e0f5a.png)

When adding bright highlights, try avoid using pure solid white. With darker colored objects, this can look somewhat graphic and flat. Using a bit of the tint from the object colors would render better.
    
![shinyrender2.png](https://cdn-production.joinhighrise.com/create-portal/shinyrender2_9c609d07aa.png)

    

### Shine lines

Sometimes on flat, shiny surfaces we see these diagonal lines of highlight. In some cases, it indicates a subtly curved surface reflecting a strong, directional light. On extremely flat surfaces, like a window, you can think of these lines as a reflection of a ray of directional light. On furniture, you may see it on windows or floors. Generally, on furniture you’ll see it applied diagonally on the side planes, and straight up and down on the ground or top plane. It’s a little bit random and probably not extremely realistic!
Because it’s not super realistic, we try to avoid using it too often, especially because the lighting can feel off and not match when mixing random assets with random strong, directional light. 

![shinyrender3.png](https://cdn-production.joinhighrise.com/create-portal/shinyrender3_2f5735dffd.png)

# Material

The material of an object determines how you highlight and shade it.  

This diagram of 3D spheres shows how the shading & highlight looks different on matte (rough) vs shiny (glossy) materials.

![materials1.jpg](https://cdn-production.joinhighrise.com/create-portal/materials1_10ccaa2ebd.jpg)


Here is an example of rendering that in vector:

![materials2.png](https://cdn-production.joinhighrise.com/create-portal/materials2_797921112e.png)

On a different shape:

![materials3.png](https://cdn-production.joinhighrise.com/create-portal/materials3_57329c77d8.png)

**Note**: 
- Matte has no or fewer highlights
- Shiny has brighter, smaller highlights
- Metallic has a shiny highlight with the darkest color being next to the highlight (bounce light)

### Metal

![materials4.png](https://cdn-production.joinhighrise.com/create-portal/materials4_6cd7ecd06a.png)


As discussed above, an object’s metallic quality (or roughness, glossiness, and reflectivity) is a basic principal of material. A more metallic material bounces more directly, so it will have brighter highlights, darker shadows (ie higher contrast), and sometimes bounce light. An easy trick to making a material more shiny or more metallic is to make it have higher contrast and more transitions in contrast. You may also find a bounce light on metallic materials. Or you may alternate a dark shadow next to a highlight, as a trick to simulate the direct reflections of metal.

![materials5.png](https://cdn-production.joinhighrise.com/create-portal/materials5_4dae006740.png)

Some examples:

![materials166.png](https://cdn-production.joinhighrise.com/create-portal/materials166_d760c13923.png)

See how the difference in rendering will make the materials of the detail appear different than the base material of the hat and shorts.

![materials7.png](https://cdn-production.joinhighrise.com/create-portal/materials7_1b1ffe5984.png)


### Silk, Leather, Shiny, Plastic-y Fabrics

These types of fabric are all just shinier versions of matte/cotton type fabrics. They aren’t as shiny as metal, but use the same principles - brighter highlight, darker shadow, sometimes a bounce light or alternating the dark and light tones.  These examples demonstrate different levels of shininess:

![materials8.png](https://cdn-production.joinhighrise.com/create-portal/materials8_a8d33dae81.png)
![materials9.png](https://cdn-production.joinhighrise.com/create-portal/materials9_35da60ac69.png)


### Materials - Shape and Draping

Material will also determine shape, weight, folds, and draping of fabric, so be aware of this while designing. References can help you learn how different material behaves: a stiff felt coat is different than a flowy, soft silk; plastic-y polyester different than cotton.  

Take a look at the differences in these three materials: wool, cotton and silk.


Wool:

![materials10.png](https://cdn-production.joinhighrise.com/create-portal/materials10_878e06f2a4.png)


Cotton:

![materials11.png](https://cdn-production.joinhighrise.com/create-portal/materials11_40f05bc95c.png)


Silk:

![materials12.png](https://cdn-production.joinhighrise.com/create-portal/materials12_ce9302dd28.png)


Taking a look at fashion illustration and clothed figure instructionals are a good resources for learning about fabric and the way it drapes and folds.


## Study and Reference Gathering

You can find a lot of info and studies on material online.  Most of it is not in our style though, so you will have to translate it!

![materials13.png](https://cdn-production.joinhighrise.com/create-portal/materials13_4a5aa5799b.png)
![materials14.png](https://cdn-production.joinhighrise.com/create-portal/materials14_1a6268e49b.png)


Sometimes an easy tip to get a quick material study closer to our style is to Image Trace the image in Illustrator.  If you’re about to start rendering a tricky material, give it a try on a reference image.

![materials16.png](https://cdn-production.joinhighrise.com/create-portal/materials16_2204b1de7d.png)
![materials17.png](https://cdn-production.joinhighrise.com/create-portal/materials17_266dfa31d1.png)
![materials18.png](https://cdn-production.joinhighrise.com/create-portal/materials18_c42c2479cc.png)
![materials19.png](https://cdn-production.joinhighrise.com/create-portal/materials19_5da04cc2a2.png)


Just remember that we don’t go for full realism in our style. We use simplification and design elements.

Further simplifying/designing some examples more toward our style:

![materials20.png](https://cdn-production.joinhighrise.com/create-portal/materials20_b72b76e067.png)
![materials21.png](https://cdn-production.joinhighrise.com/create-portal/materials21_7a662b3f61.png)
![materials22.png](https://cdn-production.joinhighrise.com/create-portal/materials22_2d6e85c4a6.png)


You can often find good references in our style by using the search term “clip art”.  You can also try “vector” or “vector art” or “illustration”. You can see on the last example a few images from the internet that came up when searching for “Amber Clip Art:”

![materials23.png](https://cdn-production.joinhighrise.com/create-portal/materials23_025aca571b.png)



## Additional examples of material

### Fur

Fur, like a human’s hair, can have many different textures, lengths, volumes, and directions.

![furexample1.png](https://cdn-production.joinhighrise.com/create-portal/furexample1_3be9403ea5.png)
![furexample2.png](https://cdn-production.joinhighrise.com/create-portal/furexample2_7616720f79.png)
![furexample3.png](https://cdn-production.joinhighrise.com/create-portal/furexample3_294ed267b8.png)
![furexample4.png](https://cdn-production.joinhighrise.com/create-portal/furexample4_b527462da3.png)


Some more examples of **fuzz/fluff texture:**

![furtextureexamples.jpg](https://cdn-production.joinhighrise.com/create-portal/furtextureexamples_2efe2db3f6.jpg)



### Holo/Iridescent

Holo/iridescent materials are quite popular and easy to style, given the colors and sparkles.  

A defining characteristic of iridescent material is the hue shifting in light and shadows and high contrast.  

![holo1.png](https://cdn-production.joinhighrise.com/create-portal/holo1_af1fb37ec9.png)
![holo2.png](https://cdn-production.joinhighrise.com/create-portal/holo2_6f1e80b94f.png)
![holo3.png](https://cdn-production.joinhighrise.com/create-portal/holo3_66c160d027.png)
![holo4.png](https://cdn-production.joinhighrise.com/create-portal/holo4_ede8adcf6f.png)
![holoexamples.jpg](https://cdn-production.joinhighrise.com/create-portal/holoexamples_81d6e0de71.jpg)


### Gold

IRL gold has lots of different hues and values.

![gold1.png](https://cdn-production.joinhighrise.com/create-portal/gold1_9862b72db3.png)

In Highrise, you may find a variety of different-looking golds as well.  
_(Note: not all examples here are the best examples to copy, but this shows what you may find out there!)_

![gold2.png](https://cdn-production.joinhighrise.com/create-portal/gold2_92f3dffead.png)


In various contexts, it makes sense to use a various colors or types of gold. 
For example, the gold coin in Highrise is our pretty classic, typical gold, but for an antique, old-looking gun, you may want to use a rustier, bronzier gold. For a delicate, light wedding gown, you may want to use a lighter, whiter gold. For a modern, trendy skirt, you may want to use something less saturated and more neutral. These are all good design choices.  

Here are some general tips for gold colors and values:

![gold3.png](https://cdn-production.joinhighrise.com/create-portal/gold3_8cb936ed12.png)


The classic HR gold works in many contexts and is basically the gold we use on the gold coin. It’s bright, saturated, has nice contrast. Gold is metallic so it will have darker shadows and a bright highlight. You may have a dark shadow next to a highlight or bounce light.There is distinct hue shift from a lemony yellow in the base highlights to a warmer yellow in the midtone, to orange in the shadows.   

![gold4.png](https://cdn-production.joinhighrise.com/create-portal/gold4_1ef2d79d9c.png)

You may change the base hue a bit for different looks but sticking to a similar value range and hue shifting from light to dark is good practice


Avoid these common mistakes: 

![gold5.png](https://cdn-production.joinhighrise.com/create-portal/gold5_da5d6d9c5a.png)


### Some additional **material examples:**


![textureexamples.jpg](https://cdn-production.joinhighrise.com/create-portal/textureexamples_131a862fa2.jpg)
