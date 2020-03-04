# shared-particle-package
This free package contains 30+ ribbon effects created via Shuriken Particle System without non-builtin script (except for the inverted collider in LMegido and Tornado areawhich was shared for free by someone else). 
They are good for magical effects like charging and buffing.

These ribbons will look broken when the transformation (position/rotation) of the prefab is animated because the transformation is not taken into account in the calculation of particle spacing interpolation of the sub-emitter. 
If you agree that the particle system interpolation dreadfully needs improvement, 
submit bug report ticket to Unity please. Smoke and Tornado effects will look weird at certain camera angle due to alpha z-fighting which is a common issue in other 3A engines either. 
It's not an issue if your game use fixed or semi-fixed camera angle.  
But if your game allows free rotation of camera, x-fighting will be very obvious once you pan the camera backward or upward.

If you know any solution to this issue (except for telling us to buy other particle engine or shaders), 
please share that for free just like we did with this asset.

If you want to adjust the speed/duration of the trails, 
change the "start lifetime" of the master emitter (big head glow) and use the same value for the "duration" of the slave/sub emitter (trail formed by smaller glow particles). 
The start lifetime value is preferably not randomized otherwise the slave emitter won't be able to sync with the master emitter accurately. 
This issue is fixed in Unity 2017.

To change the distance of the starting point of trails to the center, 
change the multiplier values of velocity over lifetime in the master emitter (you don't need to adjust the curves,
only the multiplier value at the top left corner of the curve graph). If you've increased the multiplier, 
you may also need to boost the emission so the trail particles join each other cohesively, 
change the emission rate multiplier of the slave emitter or vice versa (for the sake of performance).

To end the looping effect smoothly before Unity 5.5, deactivate the "emission" module of the "master" particle prefab instead of disabling the whole effect prefab. If there are 2 or more master prefabs, 
all emission modules of all master (but not "slave") prefabs need to be deactivated entirely. 
You only kill/deactivate the whole effect at least 2 seconds after the deactivation of the master's emission, or simply leave it be until next activation. The smooth ending by deactivating emission module is only visible in Play mode.
In Preview mode, doing so manually will kill all particles instantly. From Unity 5.5, ParticleSystem.Stop() does not kill all emitted particles immediately unless specified with extra parameter of this function.

Charge 3/3.1 and Liberate 2.2 use particle collision with plane. 
If you want to change the ground level of collision, 
adjust the y-position of the ground-ref prefab or change collision mode from plane to world.

Special thanks to "carmine" for providing a solution to inverted collider ,
but not until the code was amended with "Use UnityEngine;". 
I use box collider in "Tornado area" because the sphere collider will change the y position which is undesirable in this effect. Collider is used in Tornado area to avoid each twister from straying too far away from the camera focus. If you don't need the collision boundary, disable the "Collision" module from the master prefab and delete the "box collider".

