# Storage
We use SharedPreferences , Room or File for storage data locally.

## When do we prefer SharedPreferences, Room, File?
- We prefer to use SharedPreferences is a key/value store where you can save a data under certain key like score or for small data such as loginInfo.
- When the data more complex, and if we would like quick access to any part of it , in this case we prefer use Room Persistence Library which is the part of jetpack Library.[you can see also this link](https://developer.android.com/training/data-storage/room)
- We also prefer to use Encrypted SharedPreferences for storage sensitive data. [you can see also this link](https://developer.android.com/topic/security/data)


# What is the best practices while using SharedPreferences for us?
- When we using getSharedPreferences() to create or access sharedPreferences objects, we always use MODE_PRIVATE. That way, only your app can access the information with in the shared preferences file.
- We prefer to write helper class for manage all SharedPreferences operation like write or read data. This helper class is include generic function thus we use sharedPreferences easily.
- We don't prefer to use SharedPreferences to transfer data.
- We also recommend asynchronous like [Data Store](https://developer.android.com/topic/libraries/architecture/datastore) structure if taking long time operations.
- We prefer to create SharedPreferences is a Singleton object so you can easily get as many references as you want, it opens file only when you call getSharedPreferences first time, or create only one reference for it.
- We also remember the larger the Preference object is the longer get, commit, apply, remove and clear operations will be. So it's highly recommended to separate your data in different small objects.
