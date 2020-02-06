Pull the custom HTML templates with an `initContainer` into a `emptyDir`
volume directory, for example `/theme`. The `initContainer` spec could
look like:

```
      initContainers:
      - name: download-theme
        image: alpine/git:1.0.7
        command:
         - git
         - clone
         - "https://github.com/kinvolk/gangway-theme.git"
         - /theme
        volumeMounts:
        - name: theme
          mountPath: /theme/
```

Mount that `emptyDir` volume into your gangway container at `/theme` and
point to the `customHTMLTemplatesDir` config parameter to it:

```
customHTMLTemplatesDir: "/theme"
```
