# skilcrypt

File-based encryption utilizing GPG. There is a "daemon" that mimic EncFS.

Your hands are not tied to any OS. GPG can be installed in most major operating systems, thus you will be able encrypt and decrypt your files no matter what OS or GPG program/port you've used.

[eCryptfs](https://defuse.ca/audits/ecryptfs.htm) and [EncFS](https://defuse.ca/audits/encfs.htm) are pretty much out of the game.

# skilcrypt-daemon (inspired by EncFS)
This fellow is suitable if you constantly edit & save files and want them to be automatically encrypted and ready for transfer A.S.A.P.

Whenever files (not ending with **.gpg**) are put inside the $SOURCE_FILES folder, they will be encrypted instantly in the background without your interaction, just make sure that you've edited the $PASSWORD_FILE (`echo 'beLoud' > /tmp/pws`).

The script will run in infinite loop, it's resource friendly don't worry.

## skilcrypt Usage
Available options: encrypt, decrypt, rmsrc, rmgpg

rmsrc  --  remove the source files and leave only the encrypted one

rmgpg  --  remove the encrypted files and leave only the source one

The program can handle single/multiple filenames and paths.

```

# Make sure to "q uo te" filenames or paths that have 'sp A ces' in their names
skillcrypt encrypt random-file.tbz2 folder1 "New File.tar.gz" folder2 'New Folder'

```

## Non-interactive encryption/decryption
Non-interactive encryption and decryption is available.

Basically you combine **encrypt** or **decrypt** with **pwf** followed by the location of your password and the rest arguments are filenames or paths.

The choice is up to you if you want to use non-interactive encryption/decryption or not.

```

skilcrypt encrypt/decrypt pwf /tmp/password file1 file2 folder3

```

## NOTES (not for the daemon)
By default skilcrypt will **not overwrite** your files, no matter whether you use the encryption or decryption options.

Feel free to use the **rmgpg** and **rmsrc** options once you verified that everything is correctly encrypted/decrypted.

As I said the program will not overwrite your files, so if **foo.tar** and **foo.tar.gpg** exist in same folder and you try to encrypt **foo.tar** or decrypt **foo.tar.gpg** you won't be able to fuck up those files. The choice what to do next is up to you.
