# Blender Script: Organize Selected Meshes into Collections

This script automatically creates a collection for each selected mesh in the Blender scene. Each selected mesh is moved to its own collection named after the mesh.

## How to Use

1. Open Blender, select multiple meshes and switch to the Scripting workspace.
2. Create a new script and paste the code from `organize_meshes_to_collections.py`.
3. Run the script to automatically organize selected mesh objects into their respective collections.

## Script Description

- **Import bpy:** Imports Blender's Python API for script interaction.
- **Define the main function:** The function `create_collections_for_selected_meshes` manages the process.
- **Retrieve the current scene:** Accesses the active scene in Blender.
- **Identify selected meshes:** Filters the selected objects to include only those of type 'MESH'.
- **Iterate through selected meshes:** For each selected mesh object:
  - **Create a new collection:** A collection is created using the object's name.
  - **Link the collection to the scene:** The new collection is added to the scene's collection hierarchy.
  - **Add the object to the new collection:** The object is linked to its corresponding new collection.
  - **Unlink from other collections:** The object is unlinked from any previous collections except the new one to ensure it's only in its new collection.

This script simplifies the process of organizing assets in Blender, making it efficient to manage and navigate through complex projects.
