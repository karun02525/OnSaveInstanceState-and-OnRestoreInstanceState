# OnSaveInstanceState-and-OnRestoreInstanceState


    Alert Dialog No any manage lifecycle  onCreate() called then  onCreateDialog() created 

    The life cycle callback of activity for the above behavior will be:

    onPause() ➟ onStop() ➟ onDestroy() ➟ Same Activity Opened Again ➟ onCreate() ➟ onStart() ➟ onResume()

    onSaveInstanceState(...) or onRestoreInstanceState(...)

    onPause() ➟ onStop() ➟ onSaveInstanceState() ➟ onDestroy() ➟ Same Activity Opened Again ➟ onCreate() ➟ onStart() ➟ onRestoreInstanceState() ➟ onResume()

    override fun onSaveInstanceState(outState: Bundle) {
          super.onSaveInstanceState(outState)
          outState.putInt(KEY_ID,12)
        }
    override fun onRestoreInstanceState(savedInstanceState: Bundle) {
          super.onRestoreInstanceState(savedInstanceState)
          val id = savedInstanceState.getInt(KEY_ID,0)
    }
------------

 ### setRetainInstance(true) 
    When setRetainInstance(true) is called on a Fragment, the Fragment will not be destroyed and recreated when a configuration change occurs (like a screen rotation). Instead, it will be detached from the current activity and reattached to the new activity.
   
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // Retain the instance across configuration changes
        setRetainInstance(true);
    }

#### What is lifecycle of DialogFragment
  DialogFragment class, which is designed to better integrate with the Fragment lifecycle and provides more consistent behavior across 
  different Android versions.

   DialogFragment
   life cycle is similar to the life cycle of a fragment



    onAttach
    onCreate
    onCreateDialog
    onCreateView
    onActivityCreated
    onStart
    onResume

    screen show

    onPause
    onStop
    onDestroyView
    onDestroy
    onDetach

####  lifecycle of Activity or 2 fragments visible 

    TAGS=> MainActivity 1   =>    onCreate:
    TAGS=> Fragment 1       =>    onAttach:
    TAGS=> Fragment 1       =>    onCreate:
    TAGS=> Fragment 1       =>    onCreateView:
    TAGS=> Fragment 1       =>    onActivityCreated:
    TAGS=>  Fragment 2      =>    onAttach:
    TAGS=>  Fragment 2      =>    onCreate:
    TAGS=>  Fragment 2      =>    onCreateView:
    TAGS=>  Fragment 2      =>    onActivityCreated:
    TAGS=> Fragment 1       =>    onStart:
    TAGS=>  Fragment 2      =>    onStart:
    TAGS=> MainActivity 1   =>    onStart:
    TAGS=> MainActivity 1   =>    onResume:
    TAGS=> Fragment 1       =>    onResume:
    TAGS=>  Fragment 2      =>    onResume: 

    onPressHome 
    
    TAGS=> Fragment 1       =>  onPause:
    TAGS=>  Fragment 2      =>  onPause:
    TAGS=> MainActivity 1   =>   onPause
    TAGS=> Fragment 1       =>  onStop:
    TAGS=>  Fragment 2      =>  onStop:
    TAGS=> MainActivity 1   =>  onStop
    TAGS=> MainActivity 1   =>  onSaveInstanceState

    then on visiable
    
    TAGS=> MainActivity 1  =>  onRestart
    TAGS=> Fragment 1      =>  onStart:
    TAGS=>  Fragment 2     =>  onStart:
    TAGS=> MainActivity 1  =>  onStart:
    TAGS=> MainActivity 1  =>  onResume:
    TAGS=> Fragment 1      =>  onResume:
    TAGS=>  Fragment 2     =>  onResume:  


![alt text](https://github-production-user-asset-6210df.s3.amazonaws.com/36824081/283979292-5b652e09-5526-45c0-90fd-c89640703ff2.png)

  

