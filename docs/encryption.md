# Encryption

MMKV uses AES_CFB for encryption. The encryption keys are stored in Keychain on iOS and Android Keystore in android but if you are using your own secure storage solution, you can opt this out and save your keys there.

## encrypt

Encrypt an already created instance of MMKV.

**Arguments**

| Name             | Required | Type    | Description                                                                           |
| ---------------- | -------- | ------- | ------------------------------------------------------------------------------------- |
| cryptKey         | yes      | String  | Password to encrypt the storage                                                       |
| secureKeyStorage | no       | boolean | Set to true of you want the library to store the password securely                    |
| alias            | no       | String  | You can provide a custom alias for storage of password, by default instanceID is used |

```js
// A simple MMKV Instance();

MMKV = new MMKVStorage.Loader().
.default()
.initialize()
.getInstance();


MMKV.encrypt("encryptionKey", true, "mycustomalias");

// or if you handle the storage of key yourself

MMKV.encrypt("encryptionKey");
```

## decrypt

Removes encryption from an encrypted instance of MMKV.

```js
// Create an instance that is encrypted

MMKV = new MMKVStorage()
  .Loader()
  .default()
  .withEncryption()
  .initialize()
  .getInstance();

// Remove encryption from an encrypted instance of MMKV.

MMKV.decrypt();
```

!> Once you have decrypted an already created instance, the loader will not encrypt it when you reload the your app. If you want to encrypt again, you will now call `encrypt()`. Only new created instances are encrypted with the loader class. Once you modify that, it will have no effect. 


## changeEncryptionKey

Change the encryption key of an encrypted instance of MMKV.

**Arguments**

| Name             | Required | Type    | Description                                                                           |
| ---------------- | -------- | ------- | ------------------------------------------------------------------------------------- |
| cryptKey         | yes      | String  | Password to encrypt the storage                                                       |
| secureKeyStorage | no       | boolean | Set to true of you want the library to store the password securely                    |
| alias            | no       | String  | You can provide a custom alias for storage of password, by default instanceID is used |

```js
// Create an instance that is encrypted

MMKV = new MMKVStorage()
  .Loader()
  .default()
  .withEncryption()
  .initialize()
  .getInstance();

MMKV.changeEncryptionKey("encryptionKey", true, "mycustomalias");

// or if you handle the storage of key yourself

MMKV.changeEncryptionKey("encryptionKey");
```


!> After changing the encryption key, you will need to change your key or provide a key in the loader method above or it will throw error and not load the database.