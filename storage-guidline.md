# Storage
Android provides several options for you to save your app data. The solution you choose depends on your specific needs, such as how much space your data requires, what kind of data you need to store, and whether the data should be private to your app or accessible to other apps and the user.

We also use;
- <b>Internal file storage:</b> We store app-private files on the device file system.
- <b>External file storage:</b> We store files on the shared external file system. This is usually for shared user files, such as photos.
- <b>Shared preferences:</b> We store private primitive data in key-value pairs like score or for small data such as loginInfo.
- <b>Databases:</b> We store structured data in a private database [Room Persistence Library](https://developer.android.com/training/data-storage/room) which is the part of jetpack Library.
- <b>FileProvider :</b> If we want to share files with other apps
- We also prefer to use [Encrypted SharedPreferences](https://developer.android.com/topic/security/data)
 for storage sensitive data.

## What is the best practices while using SharedPreferences for us?
- When we using getSharedPreferences() to create or access sharedPreferences objects, we always use MODE_PRIVATE. That way, only your app can access the information with in the shared preferences file.
- We prefer to write helper class for manage all SharedPreferences operation like write or read data. This helper class is include generic function thus we use sharedPreferences easily.
- We don't prefer to use SharedPreferences to transfer data.
- We also recommend asynchronous like [Data Store](https://developer.android.com/topic/libraries/architecture/datastore) structure if taking long time operations.
- We prefer to create SharedPreferences is a Singleton object so you can easily get as many references as you want, it opens file only when you call getSharedPreferences first time, or create only one reference for it.
- We also remember the larger the Preference object is the longer get, commit, apply, remove and clear operations will be. So it's highly recommended to separate your data in different small objects.
