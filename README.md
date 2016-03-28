# skilcrypt

Three file-based encryption scripts utilizing GPG. skilcrypt-looper and skilcrypt-daemon are trying to mimic EncFS, while the skilcrypt script is the most simplistic of the three and requires manual operation all the time.

GPG can be installed in most major operating systems, thus you will be able encrypt and decrypt your files no matter what OS or GPG program/port you've used.

# skilcrypt-looper (tries to mimic EncFS)
This script basically mirrors and encrypts your files from $DECRYPTED_FILES directory into $ENCRYPTED_FILES directory. You can edit, remove, add files into $DECRYPTED_FILES dir. and have them mirrored, but (re)encrypted automatically in $ENCRYPTED_FILES dir.

This way your $ENCRYPTED_FILES dir. can be in constant sync. with some "cloud" or external device/hdd/flash drive.

Whenever $ENCRYPTED_FILES or $DECRYPTED_FILES directories become empty, the script will mirror and decrypt or encrypt the files from the one folder into the other, just make sure that you've supplied the correct GPG password for file decryption if $DECRYPTED_FILES is empty, but $ENCRYPTED_FILES has files in it.

This script is much more cpu and disk intensive than the daemon.

# skilcrypt-daemon (inspired by EncFS)
This fellow is suitable if you constantly edit & save files and want them to be automatically encrypted and ready for transfer A.S.A.P.

Whenever files (not ending with **.gpg**) are put inside the $SOURCE_FILES folder, they will be encrypted instantly in the background without your interaction, just make sure that you've edited the variable $PASSWORD_FILE. Please use the [diceware](https://en.wikipedia.org/wiki/Diceware) method for creating passwords.

The script will run in infinite loop, it's resource friendly don't worry.


[EncFS](https://defuse.ca/audits/encfs.htm) are pretty much out of the game.
