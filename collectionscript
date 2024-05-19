def create_collections_for_selected_meshes():
    # Get the current scene
    scene = bpy.context.scene
    
    # Get selected objects
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

# Run the function
create_collections_for_selected_meshes()
