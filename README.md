# Augmented Reality Markup Language (Draft)

**Augmented Reality Markup Language (ARML)** is a markup language for creating 3D and augmented reality (AR) content. Using ARML to create AR content is as easy as making a website.

* ARML describes the structure of a 3D scene using markup language
* ARML is integrated with AR SLAM algorithms
* ARML use CSS syntax to define the styles of 3D objects and models
* ARML uses JavaScript to add interactions to the AR content

The potential for ARML is huge, that so many applications across many different areas can be made. There are lots of work to be done, so any bug reports or feature requests are welcomed in [GitHub Issues](https://github.com/Dimenxion/ARML/issues).

[**Join Slack**](https://join.slack.com/t/arml-group/shared_invite/enQtMzI2OTc1NzMyMDgwLTZlYWZkODk4ZmQwZjFkOWQyYWJiNTQ5OWQwMmQ3NmVjMTExZTkzMTQ3NDc3N2EzMDI5ODI5ZTgxY2RlYjM3ZDg)

## Table of Contents

1. [Motivation](#motivation)
2. [Getting Started](#getting-started)
3. [ARML Tags](#arml-tags)
    * [`<model>`](#model)
4. [ARML Style Sheets](#arml-style-sheets)
5. [JavaScript for ARML](#javascript-for-arml)
6. [ARML Browser and Web Code Editor](#arml-browser-and-web-code-editor)

## Motivation

Augmented Reality is the future and it's super cool. However, even with Markupit or ARCore, only a small group of developers are able to learn and use AR technology to make amazing features and apps. Also, iOS and Android are not compatible right now. We hope every developers could easily use this new techonology, and the whole process of making a 3D AR app will be much simpler. Therefore, we make ARML, which is HTML for 3D/AR, to let everyone create AR contents in minutes.

## Getting Started

### A Sample ARML Document

``` html
<style>
  #model1 { z: 5; scale: 1.5; euler-y: 180; }
  #model2 { x: 3; z: 5; euler-y: 180; }
  #model3 { y: 2; scale: 0.5; }
</style>

<body>
  <model id="model1" src="models/micromonsters/micro_knight:micro_knight" onclick="onClickModel1"></model>
  <model id="model2" src="models/micromonsters/micro_knight:micro_knight" onclick="onClickModel2">
    <model id="model3" src="models/micromonsters/micro_demon:micro_demon" onclick="onClickModel3"></model>
  </model>
</body>

<script>
  function onClickModel1() {
    var model1 = $('#model1');
    model1.animate({ z: 4, scale: 2 }, 500);
    model1.trigger('animate', 'Attack');
    setTimeout(function() {
      model1.animate({ z: 5, scale: 1.5 }, 1000);
    }, 2000);
  }

  function onClickModel2() {
    $('#model2').trigger('animate', 'GetHitFront');
  }

  function onClickModel3() {
    $('#model3').trigger('animate', 'GetHit');
  }
</script>
```

Similar to the triad of web development, ARML also have three main parts:
1. An element-tree to describe the structure of 3D models and elements in the scene;
2. The style sheets to describe the visual presentation of the content;
3. A JavaScript runtime to add dynamic effects and interactions.

To see AR content made by ARML, you can download the [ARML browser](#arml-browser).

## ARML Tags

ARML elements, represented by tags, are the building blocks of ARML file. Similar to HTML tags, ARML also use attributes to provide additional information about an element.

### `<model>`

The `<model>` element defines a 3D model. The position, rotation and scale should be defined in [style sheets](#arml-style-sheets).

#### attributes

* `src [String]`: Specifies the link of the model. For now we load the model from [Unity AssetBundles](https://docs.unity3d.com/Manual/AssetBundlesIntro.html), so `src={bundleName}:{modelName}`
* `onclick [Function]`: Specifies the JavaScript function to be executed when the model is clicked

## ARML Style Sheets

ARML use a CSS-like style sheets to determine the styles of the models (position, rotation, etc). Styles should be defined within a `<style>` element.

``` html
<style>
  #model1 {
    z: 5;
    scale: 1.5;
    euler-y: 180;
  }

  #model2 { ... }
  .class-name { ... }
</style>
```

### Selectors

Selectors are patterns used to select the element. ARML will use CSS3 selectors.

| Selectors | Example       | Description                                    |
|-----------|---------------|------------------------------------------------|
| `#id`     | `#model1`     | Selects all elements with `id="model1"`        |
| `.class`  | `.class-name` | Selects all elements with `class="class-name"` |

### Properties

#### `x`, `y`, `z`
Set the `x`, `y`, `z` coordinates of the model (default `0, 0, 0`)

#### `euler-x`, `euler-y`, `euler-z`
Set the [Euler angles](https://en.wikipedia.org/wiki/Euler_angles) of the model (default `0, 0, 0`)

#### `scale`
Set the scale of the model (default `1`)

## JavaScript for ARML

ARML use JavaScript to add interactions. The script should be defined within a `<script>` element.

``` html
<script>
  function onClickModel1() {
    var model1 = $('#model1');
    model1.animate({ z: 4, scale: 2 }, 500);
    model1.trigger('animate', 'Attack');
    setTimeout(function() {
      model1.animate({ z: 5, scale: 1.5 }, 1000);
    }, 2000);
  }
</script>
```

ARML will keep the syntax similar to jQuery.

### Selectors

ARML will use the jQuery-like selectors to select elements in the scene.

* `$('#id')` will select the element with matched id.
* `$('.class-name')` will select elements by class name.

(For now, only selecting by id is supported)

### Methods

#### `.css(property, value)`
Set one CSS property for the matched element.

* `property [String]`: A CSS property name.
* `value [String|Number]`: A value to set for the property.

#### `.css(properties)`
Set a set of CSS properties for the matched element.

* `properties [Object]`: An object of property-value pairs to set.

#### `.animate(properties, duration)`
Perform a custom animation of a set of CSS properties.

* `properties [Object]`: An object of CSS properties and values that the animation will move toward.
* `duration [Number]`: A number determining how long the animation will run (in ms).

#### `.trigger(event, parameters)`
Execute an event to the matched elements, such as play an animation. For now, only `animate` event is supported.

* `event [String]`: A string containing an event type, such as `animate`.
* `parameters [String|Object]`: Additional parameters.

Events:
* `animate`: Play an animation clip once. The `parameters` should be a string determining the clip name.

## ARML Browser and Web Code Editor

[Hippo AR](https://itunes.apple.com/us/app/hippo-ar/id1241098309?mt=8) is an iOS ARML browser based on ARKit. You can test and browse AR content built by ARML on Hippo AR.

### Web Code Editor

You can check out the ARML web code editor at https://arml.hippotech.co. When first opened, it will load a sample ARML file. Modify the sample codes, or write your own ARML to make your own AR content. You can post/save it to a real location using the map next to the code editor, and test it using [Hippo AR](https://itunes.apple.com/us/app/hippo-ar/id1241098309?mt=8). Anyone who has Hippo AR can use it as the browser to view your AR content.
