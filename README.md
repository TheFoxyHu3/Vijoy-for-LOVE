# Vjoy for LÖVE

This library creates an easy virtual joystick for love2d games.

## Instalation

Just require in your script and set function, like this setup.

```lua
require "Vjoy"

function love.load()
  Vjoy = new("fixed", 100, 200, 30)
end

function love.draw()
  Vjoy.draw(...)
end

function love.update(dt)
  Vjoy.update(dt)
end

function love.touchpressed(id, x, y, dx, dy, pressure)
  Vjoy.pressed(id, x, y, dx, dy)
end

function love.touchmoved(id, x, y, dx, dy, pressure)
  Vjoy.moved(id, x, y, dx, dy)
end

function love.touchreleased(id, x, y, dx, dy, pressure)
  Vjoy.released(id, x, y, dx, dy, pressure)
end
```

## Documentation

- [**Functions**](#functions)
  - [main](#fun-main)
    - [new(mode, x, y, ray, t, activeRay, joyImg, stickImg)](#fun-new)
    - [draw(r, g, b, a, mode, r2, g2, b2, a2)](#fun-draw)
  - [set](#fun-set)
    - [setFadeTime(t)](#fun-fdtime)
    - [setJoyX(x)](#fun-joy-x)
    - [setJoyY(y)](#fun-joy-y)
    - [setJoyPosition(x, y)](#fun-joy-pos)
    - [setActiveRay(r)](#fun-act-ray)
    - [setJoyRay(r)](#fun-ray)
    - [setJoyImg(img)](#fun-joy-img)
    - [setStickImg(img)](#fun-stick-img)
  - [get](#fun-get)
    - [getAxis(dP)](#fun-gt-axis)
    - [getX(dP)](#fun-gt-x)
    - [getY(dP)](#fun-gt-y)
    - [getJoyX( )](#fun-gt-joy-x)
    - [getJoyY( )](#fun-gt-joy-y)
    - [getJoyPos( )](#fun-gt-joy-pos)
    - [getAngle( )](#fun-gt-angle)
    - [getAngleDeg( )](#fun-gt-angledg)
    - [getAngle( )](#fun-gt-angle)
    - [getActiveRay( )](#fun-gt-active-ray)
    - [getRay( )](#fun-gt-ray)
- [**Modes**](#modes)
  - [*`"fixed"`*](#md-fix)
  - [*`"free"`*](#md-free)

## Functions

<div id="fun-main"/>
<div id="fun-new" />

### *`new(mode, x, y, ray, t, activeRay, joyImg, stickImg)`*

**Example:**
```lua
Vjoy = new("fixed", 100, 200, 30, 0.1, 1.8, mageJoy, ImageSticky)
```

**Synopsis:**

This function creates a new virtual joystick

OBS: the variable declared here, in this case `Vjoy`, is used in anothers places!

**Arguments**
- `mode`: The [joyMode](#modes) of vjoy.

- `x`: The position in the x axis of the vjoy.
- `y`: The position in the y axis of the vjoy.
- `ray`: The ray of the vjoy.
- `t` *(optional)*: The "time" to joy stick go to the center. You can just set to `nil` to keep the original value.
- `activeRay` *(optional)*: The value for the active area of vjoy. This value is multiplied to the ray.
- `joyImg` *(optional)*: The image to the ray of vjoy. Get by `love.graphics.newImage`. The image will auto scaled.
- `stickImg` *(optional)*: The image to the stick of vjoy. Get by `love.graphics.newImage`. The image will auto scaled.

**Returns**
- *Nothing*

<div id="fun-draw"/>

### *`draw(r, g, b, a, mode, r2, g2, b2, a2)`*

**Example:**
```lua
function love.draw()
  Vjoy.draw(1, 0, 0.5, 1, "line", 0, 255, 125, 255)
end
```

**Synopsis:**

This function it's required for vjoy works. This function actualy returns nothing but can used to change vjoy's color and fillMode of circle (if not heave image).

If some color1 are nil, will set by 1, but if some color2 are nil, will set by color1 equivalet.

**Arguments**
- `r`: The red value in the RGB color. This it's for to the ray.

- `g`: The green value in the RGB color. This it's for to the ray.
- `b`: The blue value in the RGB color. This it's for to the ray.
- `a`: The alpha value (or opacity) applyed in the drawble.
- `mode`: The fillMode of circle, for the case the image don't heavet loaded. By normal, it's `"line"`
- `r2`: The red value in the RGB color.
- `g2`: The green value in the RGB color. This it's for to the stick.
- `b2`: The blue value in the RGB color. This it's for to the stick.
- `a2`: The red value in the RGB color. This it's for o the stick.

**Returns**
- *Nothing*

<div id="fun-set"/>
<div id="fun-fdtime"/>

### *`setFadeTime(t)`*

**Synopsis:**
This function set the number that will be set in lerp (linear interploration).

**Arguments**
- `t`: The "time" to joy stick go to the center.

**Returns**
- *Nothing*

<div id="fun-joy-x"/>

### *`setJoyX(x)`*

**Synopsis:**
This function set the position in the x axis of vjoy.

**Arguments**
- `x`: The position in the x axis of the vjoy.

**Returns**
- *Nothing*

<div id="fun-joy-y"/>

### *`setJoyY(y)`*

**Synopsis:**
This function set the position in the y axis of vjoy.

**Arguments**
- `y`: The position in the y axis of the vjoy.

**Returns**
- *Nothing*

<div id="fun-joy-pos"/>

### *`setJoyPosition(x, y)`*

**Synopsis:**
This function set the position of vjoy.

**Arguments**
- `x`: The position in the x axis of the vjoy.
- `y`: The position in the y axis of the vjoy.

**Returns**
- *Nothing*

<div id="fun-act-ray"/>

### *`setActiveRay(r)`*

**Synopsis:**
This function set the `activeRay` of vjoy. This number will multiplied by ray.

**Arguments**
- The number that will be multiplied by ray.
**Returns**
- *Nothing*

<div id="fun-ray"/>

### *`setJoyRay(r)`*

**Synopsis:**
This function set the ray of vjoy.

**Arguments**
- `r`: The ray of vjoy.

**Returns**
- *Nothing*

<div id="fun-joy-img"/>

### *`setJoyImg(img)`*

**Synopsis:**
This function set the image of joy ray. The image will auto scaled.

**Arguments**
`img`: The image of joy ray. You can get image from `love.graphics.newImage`

**Returns**
- *Nothing*

<div id="fun-stick-img"/>

### *`setStick(img)`*

**Synopsis:**
This function set the image of stick. The image will auto scaled.

**Arguments**
`img`: The image of joy ray. You can get image from `love.graphics.newImage`

**Returns**
- *Nothing*

<div id="fun-get"/>
<div id="fun-gt-axis"/>

### *`getAxis(dP)`*

**Synopsis:**
This function returns the distance of vjoy's axis.
The number is between -1 and 1, and you can set the decimal houses you wanted.

**Arguments**
- `dP`: The decimal places of number, the bigger number, more accurate.

**Returns**
- The distance of axis between -1 and 1 of stick of vjoy.

<div id="fun-gt-x"/>

### *`getX(dP)`*

**Synopsis:**
This function returns the distance in x axis of vjoy.
The number is between -1 and 1, and you can set the decimal houses you wanted.

**Arguments**
- `dP`: The decimal places of number, the bigger number, more accurate.

**Returns**
- The distance in x axis between -1 and 1 of stick of vjoy.

<div id="fun-gt-y"/>

### *`getY(dP)`*

**Synopsis:**
This function returns the distance in y axis of vjoy.
The number is between -1 and 1, and you can set the decimal houses you wanted.

**Arguments**
- `dP`: The decimal places of number, the bigger number, more accurate.

**Returns**
- The distance in y axis between -1 and 1 of stick of vjoy.

<div id="fun-gt-joy-x"/>

### *`getJoyX()`*

**Synopsis:**
This function returns the x axis position of vjoy.

**Arguments**
- *Nothing*

**Returns**
- The x position of the vjoy.

<div id="fun-gt-joy-y"/>

### *`getJoyY()`*

**Synopsis:**
This function returns the y axis position of vjoy.

**Arguments**
- *Nothing*

**Returns**
- The y position of the vjoy.

<div id="fun-gt-joy-pos"/>

### *`getJoyPosition()`*

**Synopsis:**
This function returns the position of vjoy. That's not
the stick!

**Arguments**
- *Nothing*

**Returns**
- The position x, and y of vjoy.

<div id="fun-gt-angle"/>

### *`getAngle()`*

**Synopsis:**
This function returns the angle in rad (standard unit of measurement).

![img_rad](/src/angle_rad.png)

**Arguments**
- *Nothing*

**Returns**
The angle in radians of vjoy.

<div id="fun-gt-angledg"/>

### *`getAngleDeg()`*

**Synopsis:**
This function returns the angle in degrees.

![img_deg](/src/angle_deg.png)

**Arguments**
- *Nothing*

**Returns**
- The angle in degrees of vjoy.

<div id="fun-gt-anglegd"/>

### *`getAngleGrad()`*

**Synopsis:**
This function returns the angle in grado.

![img_grado](/src/angle_grad.png)

**Arguments**
- Nothing

**Returns**
- The angle in gon (grado) of vjoy.

<div id="fun-gt-active-ray"/>

### *`getActiveRay()`*

**Synopsis:**
This function returns the `activeRay`, a number when
multiplied by ray, set the activable area of vjoy.

**Arguments**
- *Nothing*

**Returns**
- The `activeRay`

<div id="fun-gt-ray"/>

### *`getRay()`*

**Synopsis:**
This function returns the ray of vjoy.

**Arguments**
- *Nothing*

**Returns**
- The ray of vjoy.

## Modes

This library heave (for now) 2 modes to use, `"fixed"` or `"free"`.

<div id="md-fix"/>

### *`"fixed"`*
Like others virtual joystick, this mode set and put the vjoy
in the position and when touch, don't change position.

<div id="md-free"/>

### *`"free"`*
This mode set the position of center when touch inside the
`activeRay`, and return back to the previus position.

more will be added soon...
