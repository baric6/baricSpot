# Node removing dependencies

Make sure you are in the same location as your project in terminal&#x20;

Remove the node\_modules from the project

```
Remove-Item -Recurse -Force node_modules
```

Clear the npm cache

```
npm cache clean --force
```

Remove global npm packages (if removing global packages)

```
npm ls -g --depth=0
```

Clean Cache

```
npm cache clean --force
```

Audit for vulns

```
npm audit
```

