# Geometry

The geometry component provides a basic shape for an entity. The `primitive`
property defines the general shape. Geometric primitives, in computer graphics,
are irreducible basic shapes. A material component is commonly defined to
provide a appearance alongside the shape to create a complete mesh.

## Primitive

Every geometry type will have a primitive property specifies the name of a geometry.
The available geometries are listed below.

## Built-in Geometries

### `box`

The box geometry defines boxes.

```html
<a-entity geometry="primitive: box; width: 1; height: 1; depth: 1"></a-entity>
```

| Property | Description                                    | Default Value |
|----------|------------------------------------------------|---------------|
| depth    | Depth (in meters) of the sides on the Z axis.  | 1             |
| height   | Height (in meters) of the sides on the Y axis. | 1             |
| width    | Width (in meters) of the sides on the X axis.  | 1             |

### `circle`

The circle geometry creates flat two-dimensional circles. Note that because circles are flat,
ARML will only render a single face of the circle.

```html
<a-entity geometry="primitive: circle; radius: 1"></a-entity>
```

| Property    | Description                                                                                                                      | Default Value |
|-------------|----------------------------------------------------------------------------------------------------------------------------------|---------------|
| radius      | Radius (in meters) of the circle.                                                                                                | 1             |


### `cone`

The cone geometry defines cones.

```html
<a-entity geometry="primitive: cone; radius: 1; height: 0.5"></a-entity>
```

| Property       | Description                                                     | Default Value |
|----------------|-----------------------------------------------------------------|---------------|
| height         | Height of the cone.                                             | 2             |
| radius         | Radius of the bottom of the cone.                               | 1             |

### `cylinder`

The cylinder geometry creates cylinders in the traditional sense like a
Coca-Cola™ can. We can create a basic cylinder using height and radius:

```html
<a-entity geometry="primitive: cylinder; height: 3; radius: 2"></a-entity>
```

| Property       | Description                                                         | Default Value |
|----------------|---------------------------------------------------------------------|---------------|
| height         | Height of the cylinder.                                             | 2             |
| radius         | Radius of the cylinder.                                             | 1             |

### `plane`

The plane geometry creates a flat surface. Because planes are flat, ARML
will render only a single face of the plane.

```html
<a-entity geometry="primitive: plane; height: 10; width: 10"></a-entity>
```

| Property | Description              | Default Value |
|----------|--------------------------|---------------|
| height   | Height along the Y axis. | 1             |
| width    | Width along the X axis.  | 1             |

### `sphere`

The sphere geometry creates spheres (e.g., balls). We can create a basic sphere:

```html
<a-entity geometry="primitive: sphere; radius: 2"></a-entity>
```

| Property       | Description                    | Default Value |
|----------------|--------------------------------|---------------|
| radius         | Radius of the sphere.          | 1             |
