# **🔥 Godot C# Cheat Sheet: Common Classes & Properties**

This guide covers frequently used **Godot C# objects, methods, and properties**.

---

## **🎮 Input Handling**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `event is InputEventKey` | `@event is InputEventKey keyEvent` | Detects a **keyboard event**. |
| `event is InputEventMouseButton` | `@event is InputEventMouseButton mouseEvent` | Detects **mouse button events**. |
| `event is InputEventMouseMotion` | `@event is InputEventMouseMotion motionEvent` | Detects **mouse movement**. |
| `event.is_action_pressed("jump")` | `Input.IsActionPressed("jump")` | Checks if an **input action** is being held. |
| `event.is_action_just_pressed("shoot")` | `Input.IsActionJustPressed("shoot")` | Checks if an **input action** was just pressed. |
| `event.is_action_released("fire")` | `Input.IsActionJustReleased("fire")` | Checks if an **input action** was just released. |

### **Example: Handling Mouse and Keyboard Input**

```csharp
public override void _Input(InputEvent @event)
{
    if (@event is InputEventMouseButton mouseEvent)
    {
        if (mouseEvent.ButtonIndex == MouseButton.Left && mouseEvent.Pressed)
        {
            GD.Print("Left Click Pressed");
        }
    }
    
    if (@event is InputEventKey keyEvent)
    {
        if (keyEvent.Keycode == Key.Space && keyEvent.Pressed)
        {
            GD.Print("Spacebar Pressed");
        }
    }
}
```

---

## **🎭 Node and Scene System**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `get_node("Player")` | `GetNode<Node>("Player")` | Finds a node in the scene tree. |
| `add_child(node)` | `AddChild(node);` | Adds a child node. |
| `queue_free()` | `QueueFree();` | Destroys the node. |
| `get_parent()` | `GetParent<Node>();` | Gets the parent node. |
| `has_node("Enemy")` | `HasNode("Enemy")` | Checks if a node exists. |

### **Example: Spawning a Node**

```csharp
public void SpawnEnemy()
{
    PackedScene enemyScene = (PackedScene)ResourceLoader.Load("res://Enemy.tscn");
    Node2D enemyInstance = (Node2D)enemyScene.Instantiate();
    AddChild(enemyInstance);
}
```

---

## **🚀 Movement & Transforms**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `position` | `Position` | 2D Node position. |
| `global_position` | `GlobalPosition` | 2D Global position. |
| `translate(Vector2(10,0))` | `Translate(new Vector2(10, 0));` | Moves the node by an offset. |
| `rotate(deg2rad(45))` | `Rotate(Mathf.DegToRad(45f));` | Rotates the node. |
| `scale = Vector2(2,2)` | `Scale = new Vector2(2,2);` | Sets scale. |

### **Example: Moving and Rotating a Node**

```csharp
public override void _Process(float delta)
{
    Translate(new Vector2(100 * delta, 0)); // Moves right
    Rotate(Mathf.DegToRad(45f) * delta); // Rotates over time
}
```

---

## **⚡ Physics (RigidBody2D & CharacterBody2D)**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `velocity = Vector2(100, 0)` | `Velocity = new Vector2(100, 0);` | Sets velocity (for `CharacterBody2D`). |
| `move_and_slide()` | `MoveAndSlide();` | Moves a `CharacterBody2D`. |
| `apply_force(Vector2(0, 100))` | `ApplyCentralForce(new Vector2(0, 100));` | Applies force (for `RigidBody2D`). |

---

## **🖥️ UI & Control Nodes**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `text = "Hello"` | `Text = "Hello";` | Sets a `Label` or `Button` text. |
| `visible = false` | `Visible = false;` | Hides the UI element. |
| `get_tree().change_scene_to_file("res://Main.tscn")` | `GetTree().ChangeSceneToFile("res://Main.tscn");` | Changes scene. |
| `connect("pressed", self, "_on_Button_pressed")` | `MyButton.Pressed += OnButtonPressed;` | Connects a button press signal. |

### **Example: Handling Button Click**

```csharp
public void OnButtonPressed()
{
    GD.Print("Button Clicked!");
}
```

---

## **💾 Saving & Loading Data**

| **GDScript** | **C# (Godot.CSharp)** | **Description** |
|-------------|----------------------|----------------|
| `var file = FileAccess.open("user://data.save", FileAccess.WRITE)` | `using var file = FileAccess.Open("user://data.save", FileAccess.ModeFlags.Write);` | Opens a file for writing. |
| `file.store_string("Hello")` | `file.StoreString("Hello");` | Stores a string. |
| `var content = file.get_as_text()` | `string content = file.GetAsText();` | Reads file content. |

### **Example: Saving & Loading a Score**

```csharp
public void SaveScore(int score)
{
    using var file = FileAccess.Open("user://score.txt", FileAccess.ModeFlags.Write);
    file.StoreString(score.ToString());
}

public int LoadScore()
{
    if (!FileAccess.FileExists("user://score.txt")) return 0;
    using var file = FileAccess.Open("user://score.txt", FileAccess.ModeFlags.Read);
    return int.Parse(file.GetAsText());
}
```

---

This **cheat sheet** covers the **most commonly used Godot C# features**!