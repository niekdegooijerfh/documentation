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

For iOS you need to add the following to the AppDelegate

```
readonly AutoSuspendHelper autoSuspendHelper;

public AppDelegate ()
{
	autoSuspendHelper = new AutoSuspendHelper (this);
}

public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
{
	App.Initialize ();

	autoSuspendHelper.FinishedLaunching (application, launchOptions);

	return true;
}

public override void DidEnterBackground (UIApplication application)
{
	autoSuspendHelper.DidEnterBackground (application);
}

public override void OnActivated (UIApplication application)
{
	autoSuspendHelper.OnActivated (application);
}
```



