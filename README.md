EasyLoc is an Android project that lets you request location updates with a few lines of code. It also implements GooglePlayServices Location updates.

This is a simple example of how it can be used:

        LocationAdapter adapter = new LocationAdapter(this, new LocationCallback() {
            @Override
            public void locationReceived(Location location) {
                Log.i("TAG", "Location: " + location.getLatitude() + " " + location.getLongitude());
            }

            @Override
            public void playServicesConnectionStatus(int i) {
                Log.i("TAG", "PlayServices connection status: " + i);
            }

            @Override
            public void requestedLocationPlayServicesFailed() {
                Log.i("TAG", "Can not request PlayServices location updates");
            }
        });

        adapter.requestLocationUpdates(true, 0, 0, false);
        
        
With a call to requestLocationUpdates, the phone starts to get location updates from GPS and Network. You can filter location updates by <big>HIGH_ACCURACY</big> or <big>NO_POWER</big> (Google Play Services) and also by minimum update interval and minimum distance updates. It also tries to connect to Google Play Services automatically and ask them to retrieve location updates. Location updates will be received in a callback of LocationCallback.

To stop requesting updates, you must call

        adapter.stopRequestingUpdates();
        

Feel free to contribute at this project in order to make it easier and useful for all kinf of situations