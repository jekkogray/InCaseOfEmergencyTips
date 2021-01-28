# Texture Baking

January 28, 2021


## About
<p>Baking textures can be pretty intimidating, but these steps will make the process so much easier. </p>


## Baking without Project Mapping
#### Setting up
1. Go to `Shading`
1. Go to `Node Context Menu`
1. Create an `image_texture` node.
    - Name it `baked_texture_<bake_type>_<object_name>`
    - Important keep this selected, but do not connect this node.

1. Select the object you want to bake, press `Tab`
1. Go to `Object Data Properties > UV Maps`.
    - Either remove and add a new UV map. Keep it selected.

1. Go to the screen where the object is visible. Click `UV` at the top.
    1. Click `Unwrap` or `Smart Unwrap`.
    1. Ensure in UV editor this looks right.


#### Baking

1. Go to the `Render Tab` and change the `Render Engine` to `Cycles`.
    1. Adjust the settings accordingly, Click `Bake`
1. When done, there is an indicator at the bottom to let you know if it finished.
1. In UV Editor, click `Image > Save` to make sure the baked texture is saved.

#### Applying the Baked Texture

1. Select the `baked_texture_<bake_type>_<object_name>` node and connect it to an `Emission` node or connect it to the `Base Color` of the `PrincipledBSDF` node.


## Baking with Projection Mapping
#### Setting up
1. Go to `Shading`
1. Go to `Node Context Menu`
1. Create an `image_texture` node.
    - Name it `texture_<object_name>`
    - Connect this to whatever shader you want to.

1. Create an `image_texture` node.
    - Name it `baked_texture_<bake_type>_<object_name>`
    -<i> Keep this selected, but do not connect this node. <b>!!!</b> </i>

1. Select the object you want to bake, press `Tab`
1. Go to `Object Data Properties > UV Maps`.
    1. Select the first UV Map, rename to `smart_uv`
        1. Go to the screen where the object is visible. Click `UV` at the top.
        1. Click `Smart Unwrap`.
        1. Ensure in UV editor this looks right.

    1. Click on the `+` button and rename this `proj_uv`
    1. Select and make `project_uv` the Active Renderer.
        1. Go to the screen where the object is visible. Click `UV` at the top.
        1. Click `Project from View`.
        1. Modify the uv project mapping according to how you want it in `UV Editor`.
1. When done, in `Object Data Properties > UV Maps` select `smart_uv`
    -<i> Make sure it is not the active renderer. <b>!!!</b></i>

#### Baking
<blockquote>
<b>Things to Check Before Baking</b>

- Make sure <b>baked_texture_<bake_type>_<object_name></b> node is selected !!!
- Make sure <b>smart_uv</b> is selected
- Change render view to cycles.
</blockquote>

1. Go to the `Render Tab` and change the `Render Engine` to `Cycles`.
    1. Adjust the settings accordingly, Click `Bake`
1. When done, there is an indicator at the bottom to let you know if it finished.
1. In UV Editor, click `Image > Save` to make sure the baked texture is saved.

#### Applying the Baked Texture

1. Select the `baked_texture_<bake_type>_<object_name>` node and connect it to an `Emission` node or connect it to the `Base Color` of the `PrincipledBSDF` node.



