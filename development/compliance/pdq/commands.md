# Commands

#### Get the desktop files and files in folders count

```
(Get-ChildItem -Path "C:\Users\<Users>\Desktop" -File -Recurse | Measure-Object).Count
```

#### Get the desktop files only count

```
(Get-ChildItem -Path "C:\Users\<User>\Desktop" -File | Measure-Object).Count
```

#### Display only files on desktop

```
Get-ChildItem -Path "C:\Users\<User>\Desktop" -File | Select-Object -ExpandProperty Name
```

