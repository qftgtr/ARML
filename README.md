# Augmented Reality Markup Language (WIP)

**Augmented Reality Markup Language (ARML)** is a markup language for creating 3D and augmented reality (AR) content. Using ARML to create AR content is as easy as making a website.

* ARML describes the structure of a 3D scene using markup language
* ARML is integrated with AR algorithms
* ARML use CSS syntax to define the styles of 3D objects and models
* ARML uses JavaScript to add interactions to the AR content

The potential for ARML is huge, that so many applications across many different areas can be made. There are lots of work to be done, so any bug reports or feature requests are welcomed in [GitHub Issues](https://github.com/Dimenxion/ARML/issues).

[**Join Slack**](https://join.slack.com/t/arml-group/shared_invite/enQtMzI2OTc1NzMyMDgwLTZlYWZkODk4ZmQwZjFkOWQyYWJiNTQ5OWQwMmQ3NmVjMTExZTkzMTQ3NDc3N2EzMDI5ODI5ZTgxY2RlYjM3ZDg)

## Table of Contents

1. [Motivation](#motivation)
2. [Getting Started](#getting-started)
3. [ARML Primitives](#arml-primitives)
4. [ARML Components](#arml-components)
5. [ARML Style Sheets](#arml-style-sheets)
6. [JavaScript for ARML](#javascript-for-arml)
7. [ARML Browser and Web Code Editor](#arml-browser-and-web-code-editor)

## Motivation

Augmented Reality is the future and it's super cool, but even with ARKit or ARCore, only a small group of developers are able to learn and use AR and make amazing stuffs. We hope every developers could easily use AR and the whole process of making AR content will be much simpler. So we designed ARML, which is HTML for 3D/AR, to let everyone create AR contents in minutes.

## Getting Started

### A Simple ARML

``` html
<html>
  <head>
    <title>A simple ARML</title>
    <meta charset="utf-8">
    <style>
      #box {
        rotation: 0 45 0;
      }
    </style>
  </head>
  <body>
    <a-scene id="scene">
      <a-box id="box" position="-1 0.5 -3" color="#4CC3D9"></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
    </a-scene>
    <script>
      var text = document.createElement('a-text');
      text.setAttribute('value', 'Hello ARML!');
      text.setAttribute('position', '-0.5 0.5 -2.5');
      document.querySelector('#scene').appendChild(text);
    </script>
  </body>
</html>
```

You can edit the [source code](https://glitch.com/edit/#!/simple-arml?path=index.html) on glitch and play with it. ARML is compatible with [A-Frame](https://github.com/aframevr/aframe) so you can directly see what you made in browser ([preview for the above demo](https://simple-arml.glitch.me/)). A more interesting demo is [here](https://glitch.com/edit/#!/arml?path=index.html).

Similar to the triad of web development, ARML also have three main parts:
1. An element-tree to describe the structure of 3D models and elements in the scene;
2. The style sheets to describe the visual presentation of the content;
3. A JavaScript runtime to add dynamic effects and interactions.

## ARML Primitives

ARML provides a handful of elements such as `<a-box>` or `<a-model>` called *primitives*.

- [`<a-box>`](./docs/primitives/a-box.md)
- [`<a-camera>`](./docs/primitives/a-camera.md)
- [`<a-circle>`](./docs/primitives/a-circle.md)
- [`<a-cone>`](./docs/primitives/a-cone.md)
- [`<a-cursor>`](./docs/primitives/a-cursor.md)
- [`<a-cylinder>`](./docs/primitives/a-cylinder.md)
- [`<a-image>`](./docs/primitives/a-image.md)
- [`<a-light>`](./docs/primitives/a-light.md)
- [`<a-model>`](./docs/primitives/a-model.md)
- [`<a-plane>`](./docs/primitives/a-plane.md)
- [`<a-sphere>`](./docs/primitives/a-sphere.md)
- [`<a-text>`](./docs/primitives/a-text.md)
- [`<ar-plane>`](./docs/primitives/ar-plane.md)


## ARML Components

In the entity-component-system pattern, a component is a reusable and
modular chunk of data that we plug into an entity to add appearance, behavior,
and/or functionality.

In ARML, components modify entities which are 3D objects in the scene. We
mix and compose components together to build complex objects. They let us
encapsulate Unity and JavaScript code into modules that we can use
declaratively from HTML.

HTML attributes represent component names and the value of those attributes
represent component data.

### Single-Property Component

If a component is a *single-property* component, meaning its data consists of a
single value, then in HTML, the component value looks like a normal HTML
attribute:

```html
<!-- `position` is the name of the position component. -->
<!-- `1 2 3` is the data of the position component. -->
<a-entity position="1 2 3"></a-entity>
```


### Multi-Property Component

If a component is a *multi-property* component, meaning the data is consists of
multiple properties and values, then in HTML, the component value resembles
inline CSS styles:

```html
<!-- `light` is the name of the light component. -->
<!-- The `type` property of the light is set to `point`. -->
<!-- The `color` property of the light is set to `crimson`. -->
<a-entity light="type: point; color: crimson"></a-entity>
```

### List of Built-in Components

- [`position, rotation, scale`](./docs/components/position-rotation-scale.md)
- [`camera`](./docs/components/camera.md)
- [`cursor`](./docs/components/cursor.md)
- [`geometry`](./docs/components/geometry.md)
- [`material`](./docs/components/material.md)
- [`model`](./docs/components/model.md)
- [`raycaster`](./docs/components/raycaster.md)


## ARML Style Sheets

ARML use a CSS-like style sheets to easily set geometry or visual attributes of the models (position, rotation, etc). Styles should be defined within a `<style>` element.

``` html
<style>
  #model1 {
    position: 1 2 3;
    rotation: 0 180 0;
  }
</style>
```

### Selectors

Selectors are patterns used to select the element. ARML will use CSS3 selectors.

| Selectors | Example       | Description                                    |
|-----------|---------------|------------------------------------------------|
| `#id`     | `#model1`     | Selects all elements with `id="model1"`        |
| `.class`  | `.class-name` | Selects all elements with `class="class-name"` |

### Properties

#### `position`
Set the `x`, `y`, `z` coordinates of the model (default `0 0 0`)

#### `rotation`
Set the [Euler angles](https://en.wikipedia.org/wiki/Euler_angles) of the model (default `0 0 0`)

#### `scale`
Set the scale of the model (default `1 1 1`)

## JavaScript for ARML

WIP

## ARML Browser and Web Code Editor

[Hippo AR](https://itunes.apple.com/us/app/hippo-ar/id1241098309?mt=8) is an iOS ARML browser based on ARKit. You can test and browse AR content built by ARML on Hippo AR.
