# Godot 4.4 Step-by-Step Tutorial: Building Your First RPG Scene

## Part 1: Understanding the Godot Interface

When you open Godot, you'll see:
- **Scene Tree** (top-left): Shows the hierarchy of nodes in your current scene
- **Inspector** (right): Properties of the selected node
- **FileSystem** (bottom-left): Your project files
- **3D Viewport** (center): Where you build your 3D world

## Part 2: Create Your First Scene - The Main World

### Step 1: Create the Main Scene
1. Click "Add Node" (+ icon) in Scene tree
2. Search for "Node3D" and add it
3. Rename it to "Main" (right-click → rename)
4. Save the scene: Ctrl+S, name it "Main.tscn" in a new "scenes" folder

### Step 2: Add the Player Character
1. Right-click "Main" → Add Child
2. Add "CharacterBody3D" node
3. Rename to "Player"
4. With Player selected, add these children:
   - **MeshInstance3D**: Right-click Player → Add Child → MeshInstance3D
   - **CollisionShape3D**: Add this as another child of Player
   - **Camera3D**: Add this as another child of Player

### Step 3: Set Up the Player Mesh
1. Select the MeshInstance3D under Player
2. In Inspector, click "Mesh" dropdown
3. Choose "New CapsuleMesh" (this will be your temporary player body)
4. Adjust the capsule height to about 2.0 in the Inspector

### Step 4: Set Up Player Collision
1. Select CollisionShape3D under Player
2. In Inspector, click "Shape" dropdown
3. Choose "New CapsuleShape3D"
4. The shape should automatically match your mesh

### Step 5: Position the Camera
1. Select Camera3D under Player
2. In the 3D viewport, use the move tool to position it at head height
3. Or set Transform → Position to (0, 1.5, 0) in Inspector

### Step 6: Add the Player Script
1. Select the Player node
2. Click the script icon (📄) next to the node name
3. Choose "Create Script"
4. Set path to "scripts/player.gd" (create scripts folder if needed)
5. **IMPORTANT**: Delete the default script content and copy the player script I created earlier

### Step 7: Create the Ground
1. Right-click Main → Add Child → StaticBody3D
2. Rename to "Ground"
3. Add children to Ground:
   - MeshInstance3D
   - CollisionShape3D

### Step 8: Set Up Ground Mesh
1. Select Ground's MeshInstance3D
2. Set Mesh to "New BoxMesh"
3. In the BoxMesh properties, set Size to (20, 0.2, 20) for a large flat ground

### Step 9: Set Up Ground Collision
1. Select Ground's CollisionShape3D
2. Set Shape to "New BoxShape3D"
3. Adjust size to match the mesh

### Step 10: Add Lighting
1. Right-click Main → Add Child → DirectionalLight3D
2. In Inspector, rotate it to light the scene (try X: -30, Y: 45, Z: 0)
3. For that warm 2000s feeling, change the Light Color to a warm yellow/orange

### Step 11: Test Your Scene
1. Make Main.tscn your main scene: Go to Project → Project Settings → Application → Run → Main Scene
2. Set it to "res://scenes/Main.tscn"
3. Press F5 or click the Play button
4. Use WASD to move, mouse to look around, Space to jump, Escape to release mouse

## Part 3: Creating Your First NPC

### Step 1: Create NPC Scene
1. Create new scene: Scene → New Scene
2. Add CharacterBody3D as root, rename to "NPC"
3. Add children: MeshInstance3D, CollisionShape3D
4. Set up mesh and collision similar to player
5. Save as "scenes/NPC.tscn"

### Step 2: Create NPC Script
1. Attach script to NPC root node
2. Use this basic structure:

```gdscript
extends CharacterBody3D
class_name NPC

@export var character_name: String = "Mysterious Figure"
@export var dialogue_file: String = ""

func interact(player: Player) -> void:
    print("Talking to ", character_name)
    # Here you'll connect to the dialogue system later
```

### Step 3: Add NPC to Main Scene
1. Open Main.tscn
2. Right-click Main → Instance Child Scene
3. Select your NPC.tscn
4. Position the NPC somewhere near the player spawn

## Part 4: Next Steps

Now you have:
✅ A playable character with movement and camera
✅ A basic world with ground and lighting
✅ Framework for NPCs and dialogue

### Immediate Next Steps:
1. **Test everything** - Run the scene and walk around
2. **Adjust lighting** for that warm 2000s aesthetic
3. **Create more detailed meshes** or import 3D models
4. **Connect the dialogue system** to NPCs
5. **Add more environmental objects**

### For GameCube-style Graphics:
- Use **low-poly meshes** (keep vertex counts reasonable)
- Apply **simple, colorful materials** 
- Use **vertex lighting** instead of complex shaders
- Keep **bright, saturated colors**

### Common Beginner Issues:
- **Can't move**: Check if player script is attached correctly
- **Falling through ground**: Make sure collision shapes are set up
- **Camera issues**: Verify camera is child of player
- **Script errors**: Check the Output tab for error messages

Remember: Game development is iterative! Start simple, test often, and gradually add complexity. 