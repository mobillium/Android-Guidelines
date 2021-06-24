# Storage

We use SharedPreferences , Room for storage data locally.

## When do we prefer SharedPreferences or LocalStorage?
- We prefer to use SharedPreferences is a key/value store where you can save a data under certain key like score or for small data such as loginInfo.
- When the data more complex, and if we would like quick access to any part of it , in this case we prefer use Room Persistence Library which is the part of jetpack Library.
