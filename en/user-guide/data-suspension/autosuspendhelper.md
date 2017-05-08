# AutoSuspendHelper

The AutoSuspendHelper can help you in persisting your AppState.

Usage

To implement it you'l need to

PCL/General

Android

For Android you need to implement the `Android.App.Application.IActivityLifecycleCallbacks` interface. Then add the following to the Application class

```
AutoSuspendHelper suspendHelper;

public MyApplication (IntPtr javaReference, JniHandleOwnership transfer) : base (javaReference, transfer)
{
}

public void OnActivityCreated (Activity activity, Bundle savedInstanceState)
{
}

public void OnActivityDestroyed (Activity activity)
{
}

public void OnActivityPaused (Activity activity)
{
}

public void OnActivityResumed (Activity activity)
{
}

public void OnActivitySaveInstanceState (Activity activity, Bundle outState)
{
}

public void OnActivityStarted (Activity activity)
{
}

public void OnActivityStopped (Activity activity)
{
}

public override void OnCreate ()
{
    base.OnCreate ();
    
    App.Initialize ();
    
    suspendHelper = new AutoSuspendHelper (this);
}
```

iOS

