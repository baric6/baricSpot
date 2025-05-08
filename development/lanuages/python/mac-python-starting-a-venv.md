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
