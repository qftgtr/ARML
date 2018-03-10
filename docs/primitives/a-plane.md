# `<a-plane>`

[geometry]: ../components/geometry.md

The plane primitive creates flat surfaces using the [geometry][geometry]
component with the type set to `plane`.

## Example

```html
<a-plane color="#CCC" height="2" width="2"></a-plane>
```

## Attributes

| Attribute                        | Component Mapping                      | Default Value |
| --------                         | -----------------                      | ------------- |
| color                            | material.color                         | #FFF          |
| height                           | geometry.height                        | 1             |
| src                              | material.src                           | None          |
| width                            | geometry.width                         | 1             |

## Parallelizing to the Ground

To make a plane parallel to the ground or make a plane the ground itself,
rotate it around the X-axis:

```html
<a-plane rotation="-90 0 0"></a-plane>
```
