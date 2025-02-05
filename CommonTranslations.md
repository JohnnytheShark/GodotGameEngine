# Godot 2D Transformations in C# (for Nodes inheriting from Node2D)

| Transformation | GodotScript (GDScript) | C# (Godot.CSharp) | Description |
| --- | --- | --- | --- | 
| Position | position = Vector2(100, 200) | Position = new Vector2(100, 200); | Sets the node's position. |
| Rotation (Degrees) | rotation_degrees = 45 | RotationDegrees = 45f; | Sets rotation in degrees. |
| Rotation (Radians) | rotation = deg2rad(45) | Rotation = Mathf.DegToRad(45f); | Sets rotation in radians. |
| Scale | scale = Vector2(2, 2) | Scale = new Vector2(2, 2); | Scales the node. |
| Global Position | global_position = Vector2(300, 400) | GlobalPosition = new Vector2(300, 400); | Sets the node's global position. | 
| Move by Offset | translate(Vector2(10, 0)) | Translate(new Vector2(10, 0)); | Moves the node by an offset. |
| Rotate by Offset | rotate(deg2rad(15)) | Rotate(Mathf.DegToRad(15f)); | Rotates the node incrementally. |
| Flip Horizontally | scale.x = -scale.x | Scale = new Vector2(-Scale.X, Scale.Y); | Flips the node horizontally. | 
| Flip Vertically | scale.y = -scale.y | Scale = new Vector2(Scale.X, -Scale.Y); | Flips the node vertically. |
| Set Transform | transform = Transform2D(…) | Transform = new Transform2D(…); | Sets a custom transformation matrix. |
| Apply Transform | set_global_transform(…) | SetGlobalTransform(new Transform2D(…)); | Sets a global transformation. |
| Rotate Around Point | rotate_around(Vector2(100,100), deg2rad(45)) | RotateAround(new Vector2(100,100), Mathf.DegToRad(45f)); | Rotates around a specific point.| 

