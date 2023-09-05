### access the transform component of a game object

by simply writing ```transform``` in a c# script that happens to be a component on a game object

I can modify the transform component of a game object in the c# code in the following ways:

![transform-stuff.png](transform-stuff.png "transform-stuff.png")

### destroy the game object

```
Destroy(gameObject);
```

so if the class that this code is in, is added as a component it will kill the object it's on

this is why you shouldn't name GameObjects, gameObject. 

### how to quickly tell that a game object is a prefab from the hierarchy window

![how to quickly tell that a game object is a prefab from the hierarchy window](prefabs.png "how to quickly tell that a game object is a prefab from the hierarchy window")

### record game objects being moved and turn them into animations with a recorder

![animation-recorder.png](animation-recorder.png "animation-recorder.png")

### edit a keyframe of an animation already made

make sure the recorder is on when editing a keyframe

you can select the exact keyframe by hitting the fast forward and rewind buttons

![edit-keyframe-animation](edit-keyframe-animation "edit-keyframe-animation")

### how to detect two game objects touching

if both have colliders and one has a rigid body then we can detect the touch

then you can detect the collision using OnTriggerEnter

### turning-image-into-sprite.png

![turning-image-into-sprite.png](turning-image-into-sprite.png "turning-image-into-sprite.png")

### freeze-rotation.png

![freeze-rotation.png](freeze-rotation.png "freeze-rotation.png")

### switch-dim-views-in-3d-space.png

![switch-dim-views-in-3d-space.png](switch-dim-views-in-3d-space.png "switch-dim-views-in-3d-space.png")

### using assets from unity asset store

![using assets from unity asset store](using-assets-from-unity-asset-store.png "using assets from unity asset store")

### on windows hold left alt while hand tool is selected to rotate around

![on windows hold left alt](on-windows-hold-left-alt.png "on windows hold left alt")

### track collisions without blocking them (trigger)

![what is trigger true does](is_trigger_true.png "What is trigger true does")

### apply changes to a prefab
![apply changes to prefab](apply_changes_to_prefab.gif "apply changes to prefab")

### instantiate a prefab

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


### rigidbody z axis motion

the game object has to have rigidbody compocomponent added to it from the unity ui

    void Start()
    {
        rb = GetComponent<Rigidbody>();
        rb.velocity = Vector3.forward * 20; //Vector3.forward is the same as 0, 0, 1
    }

### Input.GetAxisRaw("Horizontal"); 

track the sphere when it's continuously being pressed, returns a value. getAxis returns -1, 0 or 1 (good if you want to do all the smoothing of keyboard input yourself)

    // horizontalInput = Input.GetAxisRaw("Horizontal");
    // verticalInput = Input.GetAxisRaw("Vertical");

### Input.GetKeyDown("d")

does not track the sphere when it's continuously being pressed, returns true/false. Returns true during the frame the user starts pressing down the key identified by name.

Call this function from the Update function, since the state gets reset each frame. It will not return true until the user has released the key and pressed it again.

    horizontalInput = ((Input.GetKeyDown("d") ? 1 : 0) + (Input.GetKeyDown("a") ? -1 : 0));
    verticalInput = ((Input.GetKeyDown("w") ? 1 : 0) + (Input.GetKeyDown("s") ? -1 : 0));

### Time.deltaTime;

0.000001 time between each frame. this varies based on how fast your system is. slow system will be bigger deltaTime. fast system will be smaller deltaTime

### horizontal movement for 3d obj

    if (horizontalInput != 0)
    {
        rb.velocity = new Vector3(horizontalInput * 6, rb.velocity.y, rb.velocity.z);
    }

### vertical movement for 3d obj

    if (verticalInput != 0)
    { //if up or down is pressed then enter this if
        rb.velocity = new Vector3(rb.velocity.x, verticalInput * 5, rb.velocity.z);
    }

### detect swipes for mobile

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
### test on phone while coding

install unity Remote on your android phone

connect android phone to computer

in Unity -> Edit -> Project Settings -> Editor -> Device -> Any Android Device

set build settings to android -> File -> Build Settings -> Android -> Switch Platform 

save Unity

restart Unity 

Press Play

# haven't tested yet

### pre-load ads (joao wrote this)

```
public class YomiAd
{
    public string AdUnitId;
    public bool IsReady;
    private RewardedAd rewardedAd;
    private LoadAdError error;

    public YomiAd(string adUnitId)
    {
        AdUnitId = adUnitId;
        Load();
    }

    public void Show(Action successfulCallback, Action errorCallback)
    {
        if (!IsReady || rewardedAd == null || !rewardedAd.CanShowAd())
        {
            errorCallback();
            return;
        }

        rewardedAd.Show((GoogleMobileAds.Api.Reward reward) => successfulCallback());
    }

    private void Load()
    {
        if (rewardedAd != null)
        {
            rewardedAd.Destroy();
        }

        IsReady = false;

        var adRequest = new AdRequest();
        RewardedAd.Load(AdUnitId, adRequest,
            (RewardedAd ad, LoadAdError err) =>
            {
                if (error == null)
                {
                    rewardedAd = ad;
                    rewardedAd.OnAdFullScreenContentClosed += Load;
                }
                else
                {
                    rewardedAd = null;
                }

                IsReady = true;
            });
    }
}
```

just gotta check for IsReady before showing the ad:

```
while (!rewardedAd.IsReady)
{
    await Task.Yield();
}
```

you can copy+paste the AdmobManager class too if you want.
right now I’m preloading all ads on startup. when an user watches an ad, we immediately load the next ad… even though not all ads need to be preloaded
I also checked these flags:

![preload-ads.png](preload-ads.png "preload-ads.png")

sort of worried about memory usage
