## great websites!!!

https://unity.huh.how/

## tap left or right side of screen to make move left or right

https://pressstart.vip/tutorials/2018/01/29/7/unity-mobile-touch-controls.html

## mobile joystick

https://pressstart.vip/tutorials/2018/06/22/39/mobile-joystick-in-unity.html

## multiple touch inputs on mobile

https://pressstart.vip/tutorials/2018/12/1/81/multiple-touch-inputs.html

## keep object in bounds

https://pressstart.vip/tutorials/2018/06/28/41/keep-object-in-bounds.html

## setting cursor to an image 

you'll get this error when following garbage tutorials online

Invalid texture used for cursor - check importer settings or texture creation. Texture must be RGBA32, readable, have alphaIsTransparency enabled and have no mip chain.
UnityEngine.Cursor:SetCursor (UnityEngine.Texture2D,UnityEngine.Vector2,UnityEngine.CursorMode)

copy the sprites you want to use into a texture folder in the project section of unity

then right click on them and change them to Cursor

![image](https://github.com/katpavan/unity-notes/assets/45500874/e4f20797-1cef-4bea-9d26-a165b363d7a8)

in the code

    public Texture2D cursorArrowBCell;
    public void OnPointerClick(PointerEventData eventData)
    {
        // Action to perform on click
        var go = eventData.pointerPress;

        if (go.tag == "bcelltag"){
            Cursor.SetCursor(cursorArrowBCell, Vector2.zero, CursorMode.Auto);
        }
    }
## when do you use Orthographic vs Perspective Camera. 

ortho is 2d and perspective is 3d

## search for a component through the game object hierarchy 

![image](https://github.com/katpavan/unity-notes/assets/45500874/c32410da-4e99-4382-891e-30030a299811)

## update how often FixedUpdate is called

update the Fixed Timestep

![image](https://github.com/katpavan/unity-notes/assets/45500874/c6f322e7-f26c-4a4f-ba00-8a6cd9c3e6d1)


## optimize build size

1. build the game
2. go to console and hit the top right three dots
3. click on "open editor logs"
![image](https://github.com/katpavan/unity-notes/assets/45500874/d3ed1332-630d-4965-aa10-e69d62733df7)
4. scroll down or search for "build report". you'll see a detailed list of all your assets ordered by their size.
![image](https://github.com/katpavan/unity-notes/assets/45500874/6a138967-aa1f-44db-8543-b2e06198da16)


## hide a game object, use code to show it (make it visible) 

uncheck this after clicking the game object

![image](https://github.com/katpavan/unity-notes/assets/45500874/0d66673a-36e2-449c-bd46-610f6978079c)

in the code

do this 

    public GameObject SuccessMenuPanel;

drag the GameObject into the inspector input from the scene hierarchy

then in the code you can set it hidden or visible like this:

    SuccessMenuPanel.gameObject.SetActive(true);
    SuccessMenuPanel.gameObject.SetActive(true);


## multi touch

if you put two fingers on the screen, make the ball go in between those two points

if you put three fingers on the screen, make the ball go in the center of those three points

we need to use EnhancedTouchSupport

![image](https://github.com/katpavan/unity-notes/assets/45500874/47733d9d-ca17-43dd-8f36-e964647f8806)

if there are no touches on our screen do this:

![image](https://github.com/katpavan/unity-notes/assets/45500874/ada1bafc-adc8-4421-b3b6-baa64af9e863)

looping through touches and finding the center point

![image](https://github.com/katpavan/unity-notes/assets/45500874/47d2b103-4df0-4121-bcbb-a125736a0d7e)


## cinemachine for dynamic zoom

you can allocate two positions to a camera and make sure that both positions are always in view of the camera

this way when the resolution is changed, those two points are always in view

![image](https://github.com/katpavan/unity-notes/assets/45500874/41426a82-53f1-46c6-9247-d59cc956513f)

make two empty game objects and position them left and right 
![image](https://github.com/katpavan/unity-notes/assets/45500874/ccd75ba9-d473-4440-a21d-2abbdac6acf7)

cinemachine dropdown in unity -> choose Create Target Group Camera

![image](https://github.com/katpavan/unity-notes/assets/45500874/a21b99ec-7cdf-4349-81c4-bcb323f4bb12)

![image](https://github.com/katpavan/unity-notes/assets/45500874/a6bb09d5-1bf6-42d8-b6ad-bb5c59817712)

## camera zoom adjustment

![image](https://github.com/katpavan/unity-notes/assets/45500874/a2c4e335-5c2a-40ac-b885-7a28ebc63717)

![image](https://github.com/katpavan/unity-notes/assets/45500874/42b20582-beaf-47d0-ba0d-5be51c3e8cb1)

![image](https://github.com/katpavan/unity-notes/assets/45500874/ded2de22-be25-4c68-b3b5-7cb080ee071a)


## spawning prefabs from code

![image](https://github.com/katpavan/unity-notes/assets/45500874/c5207310-980c-4591-b996-91bd7226c3a5)

![image](https://github.com/katpavan/unity-notes/assets/45500874/979c91bb-c267-4c30-8477-ae1930f92799)

Quaternion.identity is the default rotation

![image](https://github.com/katpavan/unity-notes/assets/45500874/ffbb035f-c7d0-494c-ab05-01abf21ec7c3)

## how to restart a game loop without a button or restarting the scene

![image](https://github.com/katpavan/unity-notes/assets/45500874/762ad327-7e49-422e-a850-f70d566e512b)

![image](https://github.com/katpavan/unity-notes/assets/45500874/ce0e0229-eea1-4363-be2a-3ed0a3aa79fd)

## setTimeout() but in unity

Invoke method lets you call a function after a certain number of seconds

but the method goes in quotes. it's not a reference to the function.

if you want to do a reference to the function do this:

    Invoke(nameof(functionNameGoesHere), time);

## static vs dynamic vs kinematic

static means the game object isn't moving

dynamic means it's moving and physics affects it

kinematic means it's moving but physics won't affect it (ex: gravity, spring joint)

![image](https://github.com/katpavan/unity-notes/assets/45500874/15f63cd5-89a4-4012-9d55-905cb3f4b4c2)

## swap between dynamic and kinematic

    private Rigidbody2D currentBallRigidbody;
    
    //we want physics control on the ball now that player let go of the screen
    currentBallRigidbody.isKinematic = false;
    
    //this means that the ball is taken out of physics control and is kinematic means it moves with our finger
    //we want this when the player is touching the screen so they can drag the ball without physics impacting the ball
    currentBallRigidbody.isKinematic = true;
        
## spring joint

spring joint lets us attach a 2d game object with a collider to an invisible pivot point. it will swing.

step 1 - make a static sprite (one that doesn't move)

![image](https://github.com/katpavan/unity-notes/assets/45500874/1a450b59-724f-42a7-ad45-5c2ceb3ff564)

step 2 - name it pivot

![image](https://github.com/katpavan/unity-notes/assets/45500874/954c62eb-af1b-43d5-8be5-0a1eeb9573da)

step 3 - remove the collider component on it so nothing collides with it

step 4 - for our purposes change it from a circle to a square. Click the circle thing to choose a new Sprite in the Sprite row of the Sprite Renderer Component and search for circle


![image](https://github.com/katpavan/unity-notes/assets/45500874/27c0d92e-b9ea-48e4-a7ee-bc02ee9b87cd)

step 5

![image](https://github.com/katpavan/unity-notes/assets/45500874/09fb78e7-a9e1-4ede-a47e-0788855a8815)

step 6

![image](https://github.com/katpavan/unity-notes/assets/45500874/c9647dae-bf90-4903-9566-af7e7b6749e0)

---

## creating a 2d ball with physics that bounces

unity adds a sprite renderer, 2d collider and rigid body onto the circle

![image](https://github.com/katpavan/unity-notes/assets/45500874/02cebd2b-6088-4a9c-9f96-e6cf7ec9dc2f)

![image](https://github.com/katpavan/unity-notes/assets/45500874/dd3a6a3c-881c-4b11-9be0-1120e2a452d4)

make a square, stretch it and give it a collider. it doesn't need a rigidbody.

![image](https://github.com/katpavan/unity-notes/assets/45500874/8281d9f8-c635-4ce6-b6da-c90c530b96aa)

now make a 2d physics material in your assets folder

![image](https://github.com/katpavan/unity-notes/assets/45500874/7917a289-e2e2-49cb-8f2b-6691f7c95ed8)

without doing this next step, the ball will stop when it hits the floor

![image](https://github.com/katpavan/unity-notes/assets/45500874/97b05ff9-5722-4820-9c80-efdf8b3437f7)

![image](https://github.com/katpavan/unity-notes/assets/45500874/21327792-727a-47d2-b870-c170b483323a)

## definitely use the input system package - detect touch from mobile device

tricks unity into thinking mouse clicks are actually touch inputs on the screen

this way in our code we don't have to say if using mouse do this, if using touch, do this

so whether we're using the editor or our phone, it'll work the same

step 1

![image](https://github.com/katpavan/unity-notes/assets/45500874/9cc511cc-db39-43f7-840e-d5fb33fbdc9f)

step 2

![image](https://github.com/katpavan/unity-notes/assets/45500874/3f93e56c-3cea-457d-aada-1aacb26ddd37)

step 3

![image](https://github.com/katpavan/unity-notes/assets/45500874/234aadd1-17a4-47ca-be19-0b1e6f9aaed0)

to use it in code, do this:

![image](https://github.com/katpavan/unity-notes/assets/45500874/b434910e-15f1-42f1-a74b-da240ab41e0b)

you'll see options like: position, primaryTouch (first finger that touches down. if you don't need multiTouch this is good), press, pressure, radius

![image](https://github.com/katpavan/unity-notes/assets/45500874/40e7bfa8-2c4c-4b0a-ac73-2169cdca2f56)

![image](https://github.com/katpavan/unity-notes/assets/45500874/3062b13b-ffd2-4241-b3a2-645ae7329a87)

the ReadValue() function returns a Vector2

![image](https://github.com/katpavan/unity-notes/assets/45500874/abf1aedb-c895-4a03-bd0f-324ca05ea27d)

if player isn't touching the screen get out of the update function

![image](https://github.com/katpavan/unity-notes/assets/45500874/f626a0df-4a7d-4b64-bcc3-45df1b3cddf9)

![image](https://github.com/katpavan/unity-notes/assets/45500874/fa85f30a-6190-4e67-b7d7-f201822dd4d9)

unity has a built in method to convert from screen space (touch space) to world space. this method lives on the camera. the camera has a method that will convert based on where it is in the scene

![image](https://github.com/katpavan/unity-notes/assets/45500874/9a6719a9-ce8f-4b56-a904-17fb6a20325e)

![image](https://github.com/katpavan/unity-notes/assets/45500874/0e1ada09-fcac-4e8b-98e5-8155d3590125)

ScreenToWorldPoint returns a Vector3 but can take in a Vector2

![image](https://github.com/katpavan/unity-notes/assets/45500874/0d43c5d8-302b-4981-96e2-c2243b34b7f6)



![image](https://github.com/katpavan/unity-notes/assets/45500874/1137a683-44cc-46c1-9e67-602e844fe969)


## move ball to finger on screen

put ball where finger is on screen

if you want the ball to goto where your finger on the screen is then do this but you have to make sure the ball is kinematic (no physics but moveable) and not dynamic or static. dynamic is when physics is applied to it and it's movable. static is when it stays in place.

![image](https://github.com/katpavan/unity-notes/assets/45500874/d22911b8-89a3-483a-be54-9438f4c4e2ea)

## if we aren't touching screen, but were (dragging and letting go)

then launch the ball

![image](https://github.com/katpavan/unity-notes/assets/45500874/895b5114-8660-4061-aad9-9dfeb0e1b7ea)

we know for sure the finger is on the screen here so that's where we can set isDragging to true

![image](https://github.com/katpavan/unity-notes/assets/45500874/c21574ea-0bc0-4347-badb-58f6ced43ee9)


## test on different devices from the unity editor

nothing beats testing on the phone though

![image](https://github.com/katpavan/unity-notes/assets/45500874/1eabbbca-c155-4cfe-a736-06780eb61dbc)

![image](https://github.com/katpavan/unity-notes/assets/45500874/34393ebd-7fc4-4c47-8639-850aacea2752)

## canvas (UI in Unity)

The Canvas is the area that all UI elements should be inside. The Canvas is a Game Object with a Canvas component on it, and all UI elements must be children of such a Canvas.

The Canvas area is shown as a rectangle in the Scene View. This makes it easy to position UI elements without needing to have the Game View visible at all times.

UI elements in the Canvas are drawn in the same order they appear in the Hierarchy. The first child is drawn first, the second child next, and so on. If two UI elements overlap, the later one will appear on top of the earlier one.

To change which element appear on top of other elements, simply reorder the elements in the Hierarchy by dragging them. The order can also be controlled from scripting by using these methods on the Transform component: 

* SetAsFirstSibling
* SetAsLastSibling
* SetSiblingIndex

The Canvas has a **Render Mode setting** which can be used to make it render in **screen space** or **world space.**

**World Space**
In this render mode, the Canvas will behave as any other object in the scene. The size of the Canvas can be set manually using its Rect Transform, and UI elements will render in front of or behind other objects in the scene based on 3D placement. This is useful for UIs that are meant to be a part of the world. This is also known as a “diegetic interface”.

![worldspace.jpg](worldspace.jpg "worldspace.jpg")

**Screen Space - Overlay**
This render mode places UI elements on the screen rendered on top of the scene. If the screen is resized or changes resolution, the Canvas will automatically change size to match this.

![screen-space-overlay.jpg](screen-space-overlay.jpg "screen-space-overlay.jpg")

**Screen Space - Camera**
This is similar to Screen Space - Overlay, but in this render mode the Canvas is placed a given distance in front of a specified Camera
. The UI elements are rendered by this camera, which means that the Camera settings affect the appearance of the UI. If the Camera is set to Perspective, the UI elements will be rendered with perspective, and the amount of perspective distortion can be controlled by the Camera Field of View. If the screen is resized, changes resolution, or the camera frustum changes, the Canvas will automatically change size to match as well.

There are two types of camera views in game development, Perspective (objects are smaller the farther away they are) and orthographic (all objects are the same size no matter the distance)
So when you have a Screen Space Camera set to perspective, you have UI elements that can have distance from the camera.  

This would be handy if you wanted to have say 3D elements in a UI space or like the example on the Unity article there a rotated canvas

![image](https://github.com/katpavan/unity-notes/assets/45500874/650f01a7-10f2-44e9-9412-d4824b2bbefe)

![screen-space-camera.jpg](screen-space-camera.jpg "screen-space-camera.jpg")

**canvas scaler**

![canvas-scaler.png](canvas-scaler.png "canvas-scaler.png")
![canvas-scaler-2.png](canvas-scaler-2.png "canvas-scaler-2.png")

**auto size** - for text ui elements in the canvas - it makes the font size adapt to the screen size

![image](https://github.com/katpavan/unity-notes/assets/45500874/0646cf47-b13d-4d50-af1b-de268e1db8d3)

**make a ui element in the canvas stretch across it**

![image](https://github.com/katpavan/unity-notes/assets/45500874/c9a3fdcd-38a7-4f5f-82a2-7b0350a43e5e)

**trigger function on button click**

![image](https://github.com/katpavan/unity-notes/assets/45500874/8e0ba568-b7ab-40dc-ae46-fad225f34891)

## how-to-make-a-singleton

![image](https://github.com/katpavan/unity-notes/assets/45500874/f8fc6dc6-cdf4-4f05-bb6a-df7a1db5e1de)

## OnTriggerEnter-script-needs-to-be-on-GO-with-box-collider NOT the parent object

![OnTriggerEnter-script-needs-to-be-on-GO-with-box-collider.png](OnTriggerEnter-script-needs-to-be-on-GO-with-box-collider.png "OnTriggerEnter-script-needs-to-be-on-GO-with-box-collider.png")

## access the transform component of a game object

by simply writing ```transform``` in a c# script that happens to be a component on a game object

I can modify the transform component of a game object in the c# code in the following ways:

![transform-stuff.png](transform-stuff.png "transform-stuff.png")

above code from https://www.youtube.com/watch?v=8pC3SE5PIzY

## destroy the game object

```
Destroy(gameObject);
```

so if the class that this code is in, is added as a component it will kill the object it's on

this is why you shouldn't name GameObjects, gameObject. 

## how to quickly tell that a game object is a prefab from the hierarchy window

![how to quickly tell that a game object is a prefab from the hierarchy window](prefabs.png "how to quickly tell that a game object is a prefab from the hierarchy window")

## set default animation

go into the animation controller and right click a state and set it as "Set as Layer Default State"

![image](https://github.com/katpavan/unity-notes/assets/45500874/be05f01d-7430-471d-a16f-fcd0787de871)


## record game objects being moved and turn them into animations with a recorder

![animation-recorder.png](animation-recorder.png "animation-recorder.png")

## edit a keyframe of an animation already made

make sure the recorder is on when editing a keyframe

you can select the exact keyframe by hitting the fast forward and rewind buttons

![edit-keyframe-animation](edit-keyframe-animation.png "edit-keyframe-animation")

## collision matrix
https://unity.huh.how/physics-messages/collision-matrix-2d
![image](https://github.com/katpavan/unity-notes/assets/45500874/3ae3522a-2ddc-4db7-90cf-259a23b6cb0d)

## how to detect two game objects touching

if both have colliders and one has a rigid body then we can detect the touch

then you can detect the collision using OnTriggerEnter

## turning-image-into-sprite.png

![turning-image-into-sprite.png](turning-image-into-sprite.png "turning-image-into-sprite.png")

## freeze-rotation.png

![freeze-rotation.png](freeze-rotation.png "freeze-rotation.png")

## switch-dim-views-in-3d-space.png

![switch-dim-views-in-3d-space.png](switch-dim-views-in-3d-space.png "switch-dim-views-in-3d-space.png")

## using assets from unity asset store

![using assets from unity asset store](using-assets-from-unity-asset-store.png "using assets from unity asset store")

## on windows hold left alt while hand tool is selected to rotate around

![on windows hold left alt](on-windows-hold-left-alt.png "on windows hold left alt")

## track collisions without blocking them (trigger)

![what is trigger true does](is_trigger_true.png "What is trigger true does")

## apply changes to a prefab
![apply changes to prefab](apply_changes_to_prefab.gif "apply changes to prefab")

## instantiate a prefab

the prefab has to be in a Resources folder, named exactly like that.

Resources.Load

Loads the asset of the requested type stored at path in a Resources folder.

This method returns the asset at path if it can be found, otherwise it returns null.

Note that the path is case insensitive and must not contain a file extension. All asset names and paths in Unity use forward slashes, so using backslashes in the path will not work.

You must store your asset in a Resources folder. 

the path you pass to Resources.Load will be relative to the root of the closest Resources folder. 

For example, if you have an asset at:

Assets\MyGame\Models\Resources\Category1\SomeModel

You will load it like this:

Resources.Load("Category1\SomeModel")

Specific example where you create 6 prefabs in front of the player but spaced out

    obstacle = Resources.Load<GameObject>("ObstacleObject");
    playerTransform = GameObject.FindWithTag("Player").GetComponent<Transform>(); //Every object in a Scene has a Transform. It's used to store and manipulate the position, rotation and scale of the object. Every Transform can have a parent, which allows you to apply position, rotation and scale hierarchically. 
    
    for(int i = 0; i < 5; i++){
        //Quaternion does rotations, has a w value in addition to x,y,z
        //we have it so it'll rotate to the right direction so it'll be pointed to the player
        Instantiate(obstacle, playerTransform.position + Vector3.forward * (60 + i * 60), Quaternion.Euler(0, 90, 0)); //increase the second 60 to make it easier and lessen it to make it harder. it's the distance between each obstacle. less is hard. more is easier.
    }


## rigidbody z axis motion

the game object has to have rigidbody compocomponent added to it from the unity ui

    void Start()
    {
        rb = GetComponent<Rigidbody>();
        rb.velocity = Vector3.forward * 20; //Vector3.forward is the same as 0, 0, 1
    }

## Input.GetAxisRaw("Horizontal"); 

track the sphere when it's continuously being pressed, returns a value. getAxis returns -1, 0 or 1 (good if you want to do all the smoothing of keyboard input yourself)

    // horizontalInput = Input.GetAxisRaw("Horizontal");
    // verticalInput = Input.GetAxisRaw("Vertical");

## Input.GetKeyDown("d")

does not track the sphere when it's continuously being pressed, returns true/false. Returns true during the frame the user starts pressing down the key identified by name.

Call this function from the Update function, since the state gets reset each frame. It will not return true until the user has released the key and pressed it again.

    horizontalInput = ((Input.GetKeyDown("d") ? 1 : 0) + (Input.GetKeyDown("a") ? -1 : 0));
    verticalInput = ((Input.GetKeyDown("w") ? 1 : 0) + (Input.GetKeyDown("s") ? -1 : 0));

## Time.deltaTime;

0.000001 time between each frame. this varies based on how fast your system is. slow system will be bigger deltaTime. fast system will be smaller deltaTime

## horizontal movement for 3d obj

    if (horizontalInput != 0)
    {
        rb.velocity = new Vector3(horizontalInput * 6, rb.velocity.y, rb.velocity.z);
    }

## vertical movement for 3d obj

    if (verticalInput != 0)
    { //if up or down is pressed then enter this if
        rb.velocity = new Vector3(rb.velocity.x, verticalInput * 5, rb.velocity.z);
    }

## detect swipes for mobile

https://docs.unity3d.com/ScriptReference/TouchPhase.html

Began	A finger touched the screen.
Moved	A finger moved on the screen.
Stationary	A finger is touching the screen but hasn't moved.
Ended	A finger was lifted from the screen. This is the final phase of a touch.
Canceled	The system cancelled tracking for the touch. at least one finger on the screen

    //at least one finger on the screen
    if (Input.touches.Length > 0)
    {
        Debug.Log("Input.touches.Length " + Input.touches.Length);

        //only use first touch of input
        Touch touch = Input.GetTouch(0);
        if (touch.phase == TouchPhase.Began)
        {
            startPosition = touch.position; //grab the position when the player touches the screen
            Debug.Log("startPosition " + startPosition);
        }else if (touch.phase == TouchPhase.Ended || touch.phase == TouchPhase.Canceled)
        {
            startPosition = Vector2.zero; //reset it after the swipe is done
        }
        else if (touch.phase == TouchPhase.Moved)
        {
            deltaSwipe = Vector2.zero; //reset the deltaSwipe

            if (startPosition != Vector2.zero)
            {
                //get how long the swipe currently is
                deltaSwipe = touch.position - startPosition;
            }

            //get the length of the vector with sqrMagnitude. It's faster to do it this way based on unity docs
            if (deltaSwipe.sqrMagnitude > 5000)
            {
                //get direction of swipe
                float x = deltaSwipe.x;
                float y = deltaSwipe.y;

                // if x is larger then horizontal movement 
                if (Mathf.Abs(x) >= Mathf.Abs(y)) //we prefer the x axis when they're equal
                {
                    if (x > 0)
                    { // right
                        horizontalInput = 1;
                    }
                    else //left
                    {
                        horizontalInput = -1;
                    }
                }
                else
                {//d if y is larger then vertical movement
                    if (y > 0)
                    { // up
                        verticalInput = 1;
                    }
                    else //down
                    {
                        verticalInput = -1;
                    }
                }
                startPosition = deltaSwipe = Vector2.zero;
            }
        }
    }
## test on phone while coding

install unity Remote on your android phone

connect android phone to computer

in Unity -> Edit -> Project Settings -> Editor -> Device -> Any Android Device

set build settings to android -> File -> Build Settings -> Android -> Switch Platform 

save Unity

restart Unity 

Press Play
