# Lecture 17: Character Controller

## Introduction

This lecture focuses on how to switch between different types of character controllers in Highrise Studio, enhancing the way players interact with your game.

### What Is a Character Controller in Unity?

A character controller manages how characters move within a game. It's crucial for creating lifelike and responsive movements for player characters.

## Adding Character Controller to Your Game

By default, Highrise Studio uses the **Tap to Move** controller, which lets you move your character by tapping on the screen. Additionally, we offer a **Joystick** controller, which uses a virtual joystick for movement.

<Note type="info">
Make sure you've watched [Lecture 15: Prefab Variants](https://youtu.be/1rP1C1Ks5zg) before continuing with this lecture.
</Note>

### Steps to Switch Character Controller

1. Open your **WorldScene Variant** (see [Lecture 15](https://youtu.be/1rP1C1Ks5zg) on creating a variant).
2. In the inspector panel, add the **JoystickCharacterController** component.
3. Assign audio shaders for footstep walk and run sounds.
4. Set **Movement/Movement** as the External input action to enable keyboard control for desktop users.
5. Remove the **PlayerCharacterController** component from the world scene variant.
6. Press **Play** to test the new controller setup in your scene.

## Benefits of Using Character Controllers

Character controllers make it easy and intuitive for players to move characters in your game. They provide various customization options, allowing you to tailor the gaming experience to fit your design and the player's needs.

## YouTube Tutorial


<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/V5kzvDBNQbw" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

Character controllers are vital for developing engaging and smooth gameplay. By using different types of controllers, you can significantly enhance the player's interaction with your game, making it more enjoyable and immersive.