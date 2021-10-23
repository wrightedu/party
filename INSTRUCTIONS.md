## Key Signing party instructions

These instructions will walk you through a standard key signing party.

### Make your key

Before you arrive (or at the party if this is your first time messing 
with gpg), you should have a gpg key to talk about:

```
gpg --full-generate-key
```

* Select the default keys to make (option 1)
* Use your real name and email!
* Use all the bits (4096)!
* Feel free to set an expiration of 1 (day) to 0 (no expiration)
* Use a password that you will not forget!
* If you would like upload said key to a key server:

```
gpg --export <your_email_address@example.net> | curl -T - https://keys.openpgp.org
```

### Write down your email and Key fingerprint

You will be exchanging emails and key fingerprints in order to build trust 
so make sure you have the email you used to create the key and the key 
fingerprint below:

```
gpg --fingerprint <your_email@wxample.net>
```


### Exporting Keys

You will need to export your key AND any keys you sign.

```
gpg --armor --export <email@example.net>
```

### Importing Keys

Before you sign a key or send a message you need to import their public key.

```
gpg --import <keyfile>
```

### Signing a key

To show trust in a key, first verify someone's ID (typically via two 
actual forms of ID such as driver's license and student ID).  

If the person is who they say they are then go ahead and write down their 
email address and gpg key fingerprint.  You can ask for their actual key 
later.

Once you have their key file, import it (see above), then run the following:

```
gpg --edit-key <their_email@example.net>
```

This will open gpg and allow you to edit their key, to sign it run the following
gpg commands (in the gpg text menu).

```
sign
save
```

Then export their key using the export command (above) and send their signed key 
back.

### Sending an encrypted message

To send an encrypted message, first create a `txt` message or choose some
other file to encrypt and run the following:

```
gpg --encrypt --recipient <their_email@example.net> <file_to_encrypt>
```
