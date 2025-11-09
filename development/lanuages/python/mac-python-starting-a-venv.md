# Mac - Python starting a venv

Go to the root of the project file in terminal&#x20;

```
python3 -m venv .
```

Since i am in the root folder i just call it by using the ' . '

The files and folders it should make is&#x20;

* lib
* include
* bin&#x20;
* pyvenv.cfg

<figure><img src="../../../.gitbook/assets/Screen Shot 2025-05-07 at 9.00.59 PM.png" alt=""><figcaption></figcaption></figure>

To start the venv, stay in the root directory

```
source bin/activate 
```

If it returns nothing it has started and you can start installing libs&#x20;

```
pip3 install requests
```

Check if lib is installed

```
pip3 list
```

Show which python is active during a .env

```
which python
```

#### Trouble shooting

**Problem**: libs are not installing in your .env (even after you installed them) and it is telling you the lib is unknown and have a swiggly under the import.

what is happening is that the .env is linked to the 3.13 version and even tho you added the new .env to project it will still look under the old folder because it is linked somewhere (i didn't go to far with changing links)

1. if you created a .env in another python version say 3.13 and you move to 3.14 at least mine didn't, I moved my project to a new device)&#x20;

**Easy Solution**: create a new folder with a new .env that is linked to the new version of python, and just copy and paste your project from old .env folder to new .env folder add all the libs and it should work
