Immersive Mode ANE for Adobe AIR
================================

This is a simplified version of our popular [Android Full Screen ANE](https://github.com/mesmotronic/air-ane-fullscreen) that switches your app to [immersive mode](http://developer.android.com/training/system-ui/immersive.html) (if you're running Android 4.4+) as soon as it loads and handles the appropriate focus events necessary to keep it there.

That's it.

Released under BSD license, see LICENSE for details. Requires Adobe AIR 20+.

Just give me the ANE!
---------------------

Download the latest ANE from the [releases page](https://github.com/mesmotronic/air-ane-fullscreen/releases) on GitHub.

Before you start
----------------

To avoid cropping, ensure that you're using `<fullScreen>false</fullScreen>` in your `app.xml` and `stage.displayState` is set to `StageDisplayState.NORMAL`.

Code example
------------

Using the ANE in your app couldn't be easier:

```as3
import com.mesmotronic.ane.ImmersiveMode;
import flash.display.StageDisplayState;

// Put your app into the best available full screen mode

if (!ImmersiveMode.isSupported) // Is immersive mode supported? (Android 4.4+)
{
    stage.displayState = StageDisplayState.FULL_SCREEN_INTERACTIVE;
}

trace(ImmersiveMode.immersiveWidth); // The width of the screen in immersive mode
trace(ImmersiveMode.immersiveHeight); // The height of the screen in immersive mode

// Events (should work on most versions of Android)

function focusHandler(event:Event):void
{
	trace(event.type);
} 

NativeApplication.nativeApplication.addEventListener(ImmersiveMode.ANDROID_WINDOW_FOCUS_IN, focusHandler);
NativeApplication.nativeApplication.addEventListene(ImmersiveMode.ANDROID_WINDOW_FOCUS_OUT, focusHandler);
```

Starling
--------

To use this ANE with Starling,  add `Starling.handleLostContext = true;` at the start of your ActionScript code to prevent Stage3D lost context errors breaking your app when it switches into immersive mode.

If you need to fix it, fork it!
-------------------------------

This is a free, open-source project, so if you find the ANE doesn't work as you might like with a specific device, configuration or library you're using: fork it, fix it, let us know.
