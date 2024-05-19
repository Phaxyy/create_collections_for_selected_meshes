# Blender Script: Organize Selected Meshes into Collections

This script automatically creates a collection for each selected mesh in the Blender scene. Each selected mesh is moved to its own collection named after the mesh.

## How to Use

1. **Open Blender** select your objects and switch to the Scripting workspace.
2. **Create a new script** and paste the code from `organize_meshes_to_collections.py`.
3. **Run the script** to automatically organize selected mesh objects into their respective collections.

This script simplifies the process of organizing assets in Blender, making it efficient to manage and navigate through complex projects.

## Script

```python
import bpy

def create_collections_for_selected_meshes():
    """
    Creates a collection for each selected mesh object and moves the object into the new collection.
    """
    # Get the current scene
    scene = bpy.context.scene
    
    # Get selected objects that are of type 'MESH'
    selected_objects = [obj for obj in bpy.context.selected_objects if obj.type == 'MESH']
    
    for obj in selected_objects:
        # Get the name of the object
        asset_name = obj.name
        
        # Create a new collection with the asset name
        new_collection = bpy.data.collections.new(asset_name)
        # Link the new collection to the scene
        scene.collection.children.link(new_collection)
        # Link the object to the new collection
        new_collection.objects.link(obj)
        
        # Ensure the object is unlinked from its previous collections except the new one
        for collection in obj.users_collection:
            if collection != new_collection:
                collection.objects.unlink(obj)

# Run the function to organize selected meshes into collections
create_collections_for_selected_meshes()
