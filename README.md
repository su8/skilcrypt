# skilcrypt

Want cross platform encryption and decryption program ? Read on.

Wrote these GnuPG wrappers because I wanted **not only** to encrypt my files, but to access them from other operating systems.

Originally GPG will compress the file(s) before the encryption to take place, but that's so time consuming as nearly 99% of the time is spend on compression and 1% in actual encryption !

[eCryptfs](https://defuse.ca/audits/ecryptfs.htm) and [EncFS](https://defuse.ca/audits/encfs.htm) are pretty much out of the game.


## Usage
Available options: encrypt, decrypt, rmsrc, rmgpg

rmsrc  --  remove the source files and leave only the encrypted one

rmgpg  --  remove the encrypted files and leave only the source one

The program can handle single/multiple filenames and paths.

```

# Make sure to "q uo te" filenames or paths that have 'sp A ces' in their names
skillcrypt encrypt random-file.tbz2 folder1 "New File.tar.gz" folder2 'New Folder'

```

# skilcrypt-daemon
This fellow is suitable if you constantly edit & save files and want them to be automatically encrypted and ready for transfer A.S.A.P.

Whenever files are put inside $SOURCE_FILES they will be encrypted instantly, just make sure that you've edited the $PASSWORD_FILE (`echo 'beLoud' > /tmp/pws`).

The script will run in infinite loop, it's resource friendly don't worry.

## Non-interactive encryption/decryption
Non-interactive encryption and decryption is available.

Basically you combine **encrypt** or **decrypt** with **pwf** followed by the location of your password and the rest arguments are filenames or paths.

The choice is up to you if you want to use non-interactive encryption/decryption or not.

```

skilcrypt encrypt/decrypt pwf /tmp/password file1 file2 folder3

```

## NOTES
By default skilcrypt will **not overwrite** your files, no matter whether you use the encryption or decryption options.

Feel free to use the **rmgpg** and **rmsrc** options once you verified that everything is correctly encrypted/decrypted.

As I said the program will not overwrite your files, so if **foo.tar** and **foo.tar.gpg** exist in same folder and you try to encrypt **foo.tar** or decrypt **foo.tar.gpg** you won't be able to fuck up those files. The choice what to do next is up to you.

Before invoking the **rmsrc** option I would advise you to test just one randomly encrypted file **bar.gpg** (for example) by typing `cp -r bar.gpg /tmp; gpg /tmp/bar.gpg` and once it is decrypted with the correct password you can proceed ahead and remove `skilcrypt rmsrc bar` the source file **bar** that was encrypted in **bar.gpg**.

If you supplied folder for encryption it will be crawled and any single **file** inside that folder will be standalone encrypted.

## Test
On my computer (amd athlon x3 455, 8GB DDR3 1600, Corsair ForceGT 120GB 2011) skilcrypt encrypts single **tar archive** that contains 11 000 files and is 1 GB in size in matter of 4 seconds. Repeating the same test but without `--compress-algo 0` results in ... 5 minutes.

Now I can upload the encrypted files to any "cloud", encrypt/decrypt them in my smartphone and re-upload them. Also my hands are not tied to XYZ operating system.
