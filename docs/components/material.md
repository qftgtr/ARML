# Material

[geometry]: ./geometry.md

The material component gives appearance to an entity. We can define properties
such as color, opacity, or texture. This is often paired with the [geometry
component][geometry] which provides shape.

## Example

Defining a red material using the default standard material:

```html
<a-entity geometry="primitive: box" material="shader: standard; color: red"></a-entity>
```

## Built-in Shaders

ARML ships with a couple of built-in shaders.

### `standard` (default)

The `standard` material is the default shader. It uses the Unity's
[Standard Shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) which supports
[Physically-based rendering (PBR)](#physically-based-rendering).

#### Properties

These properties are available on top of the standard shader.

| Property          | Description                                                                                                                           | Default Value |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------|---------------|
| color             | Base diffuse color.                                                                                                                   | #fff          |
| emissive          | The color of the emissive lighting component. Used to make objects produce light even without other lighting in the scene.            | #000          |
| emissiveIntensity | Intensity of the emissive lighting component.                                                                                         | 1             |
| metalness         | How metallic the material is from `0` to `1`.                                                                                         | 0.5           |
| preset            | Predefined preset to set physically correct color, metalness and roughness                                                            | none          |
| roughness         | How rough the material is from `0` to `1`. A rougher material will scatter reflected light in more directions than a smooth material. | 0.5           |
| width             | Width of video (in pixels), if defining a video texture.                                                                              | 640           |
| src               | Image texture map, an inline URL.                                                                                                     | None          |

#### Physically-Based Rendering

(Physically-based rendering)[https://en.wikipedia.org/wiki/Physically_based_rendering]
is a shading model that aims to make materials behave
realistically to lighting conditions. Appearance is a result of the interaction
between the incoming light and the properties of the material.

To achieve realism, the diffuse `color`, `metalness`, `roughness` properties of
the material must be accurately controlled, often based on real-world material
studies. Some people have compiled charts of realistic values for different
kinds of materials that we can use as a starting point.

ARML ships with some presets of common materials with the physically correct
color, metalness and roughness.

```html
<a-entity geometry="primitive: cylinder" material="preset: gold;"></a-entity>
```

| Preset   | Color              | metalness | roughness |
|----------|--------------------|-----------|-----------|
| aluminum | rgb(245, 246, 246) | 1.0       | 0.1       |
| cobalt   | rgb(211, 210, 207) | 1.0       | 0.1       |
| copper   | rgb(250, 208, 192) | 1.0       | 0.1       |
| gold     | rgb(255, 225, 155) | 1.0       | 0.1       |
| iron     | rgb(196, 199, 199) | 1.0       | 0.1       |
| nickel   | rgb(211, 203, 190) | 1.0       | 0.1       |
| platinum | rgb(213, 208, 200) | 1.0       | 0.1       |
| silver   | rgb(252, 250, 245) | 1.0       | 0.1       |
| titanium | rgb(193, 186, 177) | 1.0       | 0.1       |

### `refractive`

The `refractive` shader render a transparent and refractive material, such as glass or gems.

#### Properties

These properties are available on top of the refractive shader.

| Property          | Description                                                                  | Default Value |
|-------------------|------------------------------------------------------------------------------|---------------|
| color             | Base color.                                                                  | #fff          |
| reflection        | How reflective the material surface is (from `0` to `1`)                     | 0.05          |
| ior               | Index of refraction.                                                         | 2.4           |
| aberration        | [Chromatic aberration](https://en.wikipedia.org/wiki/Chromatic_aberration)   | 0.005         |
