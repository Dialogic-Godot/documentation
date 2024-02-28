
<div class="header-banner pineapple">
     <div class="header-label pineapple">Layered Portraits</div>
</div>

*This page describes how to create layered portraits.*

## 📜 Content
[toc]

## 1. Introduction

If you want to have a character with multiple layers, like a body, a head, and
a mouth, you can use the **Layered Portrait** feature.

Dialogic uses the concept of Godot scenes to create portraits. The layered portrait feature provides us with a GDScript that you can use for this purpose.

If you are eager to learn more about the requirements for creating a custom portrait, please refer to the [Custom Portraits](custom-portraits.md) page.


## 2. Rundown

You will learn to create a new character, add a new portrait, and then create a
new Godot scene for the custom scene of this portrait.


## 3. Creating a new Character

The goal for this chapter is to create a new character with a portrait.

First, head over to the Dialogic Character tab. You will need to create
yourself a new character or edit an existing one.

Each character can have multiple portraits. You can add a new portrait or use
an existing one.

Heading over to the last segment of the Character Editor, you will find the
preview and the **Portrait Settings**.\
Unfold the **Scene** option, and you will see a file picker. Remember this
part, and later, we will provide the path of our new scene file to this picker.


## 4. Creating a Portrait Scene

Now, we want to create a new scene in the **FileSystem** tab of Godot.
We recommend creating a new folder for your portrait scenes, so you can keep
your project organized.

Right-click on the folder and hover **Create New**, and click **Scene...* on the
follow-up menu.

Select the **Root Type**, we recommend using a **2D Scene**. The **Scene Name**
is up to you, but once again, we recommend keeping your project organized with
a consistent naming scheme.

Once you press **OK**, your new scene will be opened in the **Scene** tab of
Godot. Switch to the **2D** tab in the upper-middle of Godot and you will see
your new scene.


## 4.1 Adding the Layered Portrait GDScript

To use your scene as a layered portrait, we will add a built-in
GDScript to the root node of your scene.

Right-click on the root node and hover over **Attach Script**. You can copy the
following path and paste it into the **Path** field:

```
res://addons/dialogic/Modules/Character/LayeredPortrait/layered_portrait.gd
```

Press **Load** and... that's it! You have now added the Layered Portrait
scripting logic; now onto the fun part!


## 4.2 Adding the Layers

Your layered portrait can have multiple layers. We recommend using `Node2D` as
grouping layers, and `Sprite` as the actual layers.


## 4.3 Setting the Layered Portrait Scene

Remember the file picker in the Character editor? Now is the time to use it!
Copy the path of your scene file and paste it into the file picker or navigate
to your scene file.

Once you have selected your scene file, you should be able to see your portrait
in the Character Editor's Preview.


## 5. Controlling the Layers

As of right now, you can use the `Character` event to control the layers.
The functionality is limited to the `join` and `update` variants of this event.

In Dialogic, this event accepts a parameter called `extra_data`. Using the Layer
Command Syntax, you can control the portraits from timelines.

Take a look at this example:
```tml
join princess (default) 2 [animation="Heartbeat" extra_data="show Group1"]

update princess [extra_data="set Group1/Layer1"]]
```

## 5.1 Layer Command Syntax

Here is an example of valid syntax for the `Character` event:

```tml
# Show an entire group:
show Group1

# Show a layer, does not hide others:
show Group1/Layer1

# Hide a group:
hide Group1

# Hide a layer:
hide Group1/Layer1

# Show only one layer and hide the others:
set Group1/Layer1
```

If you want to use multiple commands in one `extra_data` parameter, you can
separate them with a comma:

```tml
update princess [extra_data="set Group1/Layer1, set Group2/Layer3"]]
```

