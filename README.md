# Input.GetAxisRaw("Horizontal"); 

track the sphere when it's continuously being pressed, returns a value. getAxis returns -1, 0 or 1 (good if you want to do all the smoothing of keyboard input yourself)

    // horizontalInput = Input.GetAxisRaw("Horizontal");
    // verticalInput = Input.GetAxisRaw("Vertical");

# Input.GetKeyDown("d")

does not track the sphere when it's continuously being pressed, returns true/false. Returns true during the frame the user starts pressing down the key identified by name.

Call this function from the Update function, since the state gets reset each frame. It will not return true until the user has released the key and pressed it again.

    horizontalInput = ((Input.GetKeyDown("d") ? 1 : 0) + (Input.GetKeyDown("a") ? -1 : 0));
    verticalInput = ((Input.GetKeyDown("w") ? 1 : 0) + (Input.GetKeyDown("s") ? -1 : 0));

# Time.deltaTime;

0.000001 time between each frame. this varies based on how fast your system is. slow system will be bigger deltaTime. fast system will be smaller deltaTime

# detect swipes for mobile

https://docs.unity3d.com/ScriptReference/TouchPhase.html

Began	A finger touched the screen.
Moved	A finger moved on the screen.
Stationary	A finger is touching the screen but hasn't moved.
Ended	A finger was lifted from the screen. This is the final phase of a touch.
Canceled	The system cancelled tracking for the touch. at least one finger on the screen

    Touch touch = Input.GetTouch(0);

    //A finger touched the screen.
    if(touch.phase == TouchPhase.Began) {...}

# test on phone while coding

install unity Remote on your android phone

connect android phone to computer

in Unity -> Edit -> Project Settings -> Editor -> Device -> Any Android Device

set build settings to android -> File -> Build Settings -> Android -> Switch Platform 

save Unity

restart Unity 

Press Play

