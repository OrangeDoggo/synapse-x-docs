# Drawing Library

## Drawing New
```syn
<object> Drawing.new(<string> type)
```
Creates a new drawing object with `type`. Returns the object.
## Fonts
The following fonts are available within the `Drawing.Fonts` table.
|Font       |Number     |
|-----------|-----------|
|UI         |0          |
|System     |1          |
|Plex       |2          |
|Monospace  |3          |
|Base       |Properties |
```syn
bool Visible;
int ZIndex;
number Transparency;
Color3 Color;
void Remove();
```
Notes:

* All other classes derive from this base class.
* Transparency is the opposite than on normal GUI elements - 1 means fully opaque, while 0 means fully transparent.
* ZIndex's are **32 bit integers** - you can only use whole numbers from -2,147,483,647 to 2,147,483,647. All objects by default have a ZIndex of zero.
    * Related to that, the object rendering order goes from the lowest ZIndex to the highest. This means ZIndex's of lower values will render first, and higher will render after.
        * In more laymen terms, this means an object with a higher ZIndex will render above one with a lower ZIndex.
    * In a single ZIndex, the render order is 'first come first serve' - the oldest objects in the same ZIndex will be rendered first. Switching to a different ZIndex will kick that object back to the end of the rendering order for that ZIndex. Newly allocated objects will also start at the end of the rendering order for that specific ZIndex.

## Types:

### Line
```syn
number Thickness;
Vector2 From;
Vector2 To;
```
### Text
```syn
string Text;
number Size;
bool Center;
bool Outline;
Color3 OutlineColor;
Vector2 Position;
readonly<Vector2> TextBounds;
Drawing.Font Font;
```
### Image
```syn
writeonly<string> Data;
Vector2 Size;
Vector2 Position;
number Rounding;
```
Notes:
* `Data` does **NOT** refer to the URL of the image. You must grab the image data yourself (`game:HttpGet`), then assign that to `Data`.

### Circle
```syn
number Thickness;
number NumSides;
number Radius;
bool Filled;
Vector2 Position;
```
### Square
```syn
number Thickness;
Vector2 Size;
Vector2 Position;
bool Filled;
```
### Quad
```syn
number Thickness;
Vector2 PointA;
Vector2 PointB;
Vector2 PointC;
Vector2 PointD;
bool Filled;
```
*Notes*:
* The points are in counter-clockwise order - PointA is top-right, PointB is top-left, PointC is bottom-left, PointD is bottom-right.

### Triangle
```syn
number Thickness;
Vector2 PointA;
Vector2 PointB;
Vector2 PointC;
bool Filled;
```

## Example
```lua
local Line = Drawing.new("Line")
Line.Visible = true
Line.From = Vector2.new(0, 0)
Line.To = Vector2.new(200, 200)
Line.Color = Color3.fromRGB(255, 255, 255)
Line.Thickness = 2
Line.Transparency = 1
LIne.ZIndex = 1

wait(5)

Line:Remove() --Drawing objects are manually managed.
```