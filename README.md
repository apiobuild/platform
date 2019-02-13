# Description

This is a repo to generate static marketing website for Squared.

# Deployment

If your local is not setup - 

```shell
npm install -g firebase-tools
firebase login
firebase init
firebase use --add day-bed
```

You'd also need to install hugo first

``` shell
hugo && firebase deploy
```