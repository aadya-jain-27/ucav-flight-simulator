# ucav-flight-simulator
1. Introduction

This project is a physics-based simulation of a single Unmanned Combat Aerial Vehicle (UCAV), developed using Unity 2022 and C#. The goal was to simulate realistic aerial drone behavior, including basic combat functionality, for research and educational purposes.

2. Tools & Technologies Used

• Unity 2022 – Game engine for real-time 3D simulation.
• C# – Primary programming language for scripting.
• Visual Studio – IDE used for script development.
• Platform – macOS.

3. Features Implemented

• Takeoff and Descent: The drone can ascend (I key) and descend (K key) using keyboard input, controlled by applying vertical forces.
• Directional Movement: Uses W, A, S, D keys for forward, backward, and lateral movement.
• Yaw Rotation: The drone can rotate left or right (J and L keys) around the Y-axis.
• Tilt Visuals: Visual roll and pitch are added to simulate realistic banking and forward tilt during movement.
• Terrain Collision Prevention: Drone is prevented from going below the terrain level using raycast sampling.
• Auto-Braking: When no input is given, the drone gradually slows down its motion and angular velocity.
• Physics-Based Motion: Rigidbody physics is used to simulate natural drone motion and collision handling.
• Bullet Firing: Pressing Q fires bullets from the drone’s gun using a prefab.
• Bullet Hole Effects: Bullet impact is detected using raycasting and instantiates bullet hole prefabs on hit surfaces.
• Drone Audio: The drone's sound pitch increases with speed, providing audio feedback.

4. Script Overview

4.1 DroneMovementScript.cs
Handles all aspects of drone movement, rotation, tilt, and sound:
• Vertical lift via “upForce”.
• Forward/backward/sideways movement.
• Yaw rotation using smooth damping.
• Clamping of max speed for realism.
• Sound pitch tied to velocity.

4.2 DroneGunScript.cs
• Fires bullets on pressing Q with a delay between shots.
• Bullets are instantiated using a prefab at a defined gun transform.

4.3 BulletScript.cs
• Adds forward force to bullets.
• Uses raycasting to detect impacts.
• Instantiates bullet hole prefabs and handles destruction logic.

4.4 CameraFollowScript.cs
• Smoothly follows the drone from behind.
• Aligns with the drone’s yaw for dynamic tracking.


5. Challenges Faced

During the development of the drone simulator, several technical challenges arose:
• Unreliable Terrain Collision: Initially, the terrain collider was inconsistent — sometimes the drone correctly recognized the ground and stopped descending, but at other times it would pass through. This required tweaking physics settings and checking collider layers.
• Drone Not Lifting: A major issue was that the drone would not ascend even after applying upward force. The problem stemmed from the imbalance between the Rigidbody’s mass, gravity scale, and the applied upForce. This took considerable trial and error to tune correctly.
• Mass-to-Gravity Ratio: Tuning the Rigidbody's mass relative to Unity’s gravity settings significantly affected flight behavior. A small mismatch would result in either the drone being too sluggish or unrealistically floaty.
• Excessive Movement Speed: In the early stages, the drone moved too fast in all directions, making it hard to control. The simulator lacked smooth acceleration and deceleration, so speed clamping and damping had to be added to create realistic responsiveness.

6. Conclusion

The drone simulator successfully demonstrates key mechanics of an unmanned combat drone, combining physics-based flight, user input, and combat simulation. It provides a basic yet solid foundation for further enhancement such as multi-drone
simulation, AI-controlled drones, or networked combat scenarios. 

7. Future Enhancements

• Add enemy drones or targets.
• Integrate UI elements like health, ammo count, and radar.
• Expand to multiplayer drone battles.
