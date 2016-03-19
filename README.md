# skilcrypt

Want cross platform encryption and decryption program ? Read on.

Wrote this GnuPG wrapper because I wanted **not only** to encrypt my files, but to access them from other operating systems.

skilcrypt does really fast encryption and I stand behind this statement. Your files are secure enough as long as you use long and strong password.

Originally GPG will compress the file(s) before the encryption to take place, but that's so time consuming as nearly 99% of the time is spend on compression and 1% in actual encryption !

That's why I decided that the disk saving trade-off is not worth and added `--compress-algo 0` in skilcrypt to tell GPG not to compress the file(s). Feel free to compress your files afterwards if you want to.

You won't have access to X operating system all the time, and the need to encrypt/decrypt and use your files in Z operating system will force you to seek cross platform encryption.

Here are some real facts that made me to write skilcrypt:  I was abroad for half year and realised how limited LUKS is, as I wasn't able to access my files as I had only smartphone. The ironic thing is that the encrypted files was stored on microsd card.

[eCryptfs](https://defuse.ca/audits/ecryptfs.htm) and [EncFS](https://defuse.ca/audits/encfs.htm) are pretty much out of the game.

As long as you have access to GnuPG or any program based on GnuPG you will be able to encrypt and decrypt your files, no matter wheter you used skilcrypt or not.

## Usage
By default skilcrypt will **not overwrite** your files, no matter wheter you use the encryption or decryption options.

Feel free to use the **rmgpg** and **rmsrc** options once you verified that everything is correctly encrypted/decrypted.

As I said the program will not overwrite your files, so if **foo.tar** and **foo.tar.gpg** exist in same folder and you try to encrypt **foo.tar** or decrypt **foo.tar.gpg** you won't be able to fuck up those files. The choice what to do next is up to you.

Before invoking the **rmsrc** option I would advise you to test just one randomly encrypted file **bar.gpg** (for example) by typing `gpg bar.gpg` and once it is decrypted with the correct password you can proceed ahead and remove `skilcrypt rmsrc bar` the source file **bar** that was encrypted in **bar.gpg**.

## Test
On my computer (amd athlon x3 455, 8GB DDR3 1600, Corsair ForceGT 120GB 2011) skilcrypt encrypts single **tar archive** that contains 11 000 files and is 1 GB in size in matter of 4 seconds. Repeating the same test but without `--compress-algo 0` results in ... 5 minutes.
