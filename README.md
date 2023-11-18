# OnSaveInstanceState-and-OnRestoreInstanceState



# The life cycle callback of activity for the above behavior will be:

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

#### What is lifecycle of DialogFragment
   DialogFragment
   life cycle is similar to the life cycle of fragment


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
