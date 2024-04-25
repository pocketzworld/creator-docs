# Creating Your First World

## Introduction

This guide will walk you through the process of creating your first virtual world using Highrise Studio. You will learn how to install the necessary tools, create a simple world, add assets and lighting, and test it in Unity. The guide also covers uploading your world to the Highrise Creator Portal, updating its details, and releasing it to the public.

## Steps

### Step 1: Set Up the Tools

1. Download and install [Studio Hub](https://create.highrise.game/highrise-studio).
2. Follow Studio Hub's instructions to download and install Unity and the Highrise Studio Package.

### Step 2: Create a New World

1. In Studio Hub, click `New Project`.
2. Select the **Basic Template**.
3. Name the project "My First World".
4. Leave the location as default and click `Create Project`.

### Step 3: Use Unity

1. Sign in to your Highrise account using the `Sign In` button.
2. Test your world using the `Play` button in the top toolbar.

![Play button](/assets/learn/guides/studio/play-button.png)

### Step 4: Make Changes

1. Move and change objects:
   - Select the Green Block and drag it to move move it around the scene.
   - Alternatively, you can change the positional values in the inspector panel to the right of the scene.
   - Change the Green Block's scale to 0.5, 0.5, 0.5 in the inspector.

2. Adding an object: 
   - You can add objects to your world using the [Highrise Asset Catalog](https://create.highrise.game/learn/studio/create/assets/using-highrise-catalog.md), [Unity Asset Store](https://create.highrise.game/learn/studio/create/assets/using-unity-store.md), or manual import.
   - Select a premade asset from the Highrise Catalog.
   - Click on the Install button on the asset.
   - Wait until the download finishes.
   - Now you can drag the object directly into your world.

![Highrise Asset Catalog](/assets/learn/guides/studio/creating-your-first-world/asset-catalog.png)

3. Update the walkable area:
   - Select the NavMesh in the Hierarchy view.
   ![NavMesh](/assets/learn/guides/studio/creating-your-first-world/navmesh.png)
   - In the inspector, click `Bake`.

4. Add scripts:
   - In the Project window, navigate to the desired location.
   - Right-click and select `Create > Lua > Script`
   - Create a Lua script named "Rotate".
   - Add the following code:
     ```lua
     function self:Update()
       local rotationAngle = 5 * Time.deltaTime
       self.transform.localEulerAngles = self.transform.localEulerAngles + Vector3.new(0, rotationAngle, 0)
     end
     ```
   - Uncheck `Static` for the Green Block in the inspector.
   ![Static](/assets/learn/guides/studio/creating-your-first-world/static.png)
   - Add the "Rotate" script to the Green Block using `Add Component`.
   ![Add Component](/assets/learn/guides/studio/creating-your-first-world/add-component.png)

### Step 5: Adjust Lighting

1. Open the Lighting window via `Window > Rendering > Lighting` or `(CMD/CTRL) + 9`.
2. Add lights and set their type to `Baked`.
3. For stationary meshes, mark them as `Static`.
4. For animated or moving meshes, create a Light Probe Grid.
5. Bake the lights by clicking `Generate Lighting`.

### Step 6: Test

1. Enter Play Mode.
2. Verify your avatar appears and behaves as expected.
3. Add Virtual Players via `Highrise > Studio > Virtual Player`.
![Virtual Player](/assets/learn/guides/studio/creating-your-first-world/virtual-player.png)
4. Walk around and test the world.
5. Exit Play Mode.

### Step 7: Upload

1. Click `Upload` and select `Upload to a New World`.
![Upload](/assets/learn/guides/studio/creating-your-first-world/upload-world.png)
2. The world will be processed and available as a private draft.
3. You can now see the world in your Highrise app under "My Worlds" in the world directory.

### Step 8: Update Description and Images

1. Navigate to the page of the newly created world on the [Creator Portal Dashboard](https://create.highrise.game/dashboard/creations).
2. Click `...` and select `Edit World`.
![Edit](/assets/learn/guides/studio/creating-your-first-world/edit-world.png)
3. Update the name, introduction, and description.
4. Upload an icon and sample images.
5. Click `Save`.

### Step 9: Release

In the Builds tab of the world page, click `Release` to make your world public. This will make it available to everyone in Highrise.

## Conclusion

Congratulations! You've Created Your First World

That's it! You've successfully created your first World using the Highrise Studio. Now, you can continue to build and customize your virtual world with rooms, models, and more. Continue to part 2 of this guide to learn how to publish and release the World you've just built.

