# GitCheckouter

A simple git checkout log for Slack

## Register GitCheckouter in slack

- Go to Apps in slack
- Search for GitCheckouter
- Apply for The gitCheckouter application
- Create a new Webhook URL and choose which channel or DM you like to post to
- Use the webhook URL in your `.git/hooks/` files

## Examples

In the following examples the webhook url is a dummy. Use the one you created in the steps above

### .git/hooks/post-checkout

```
#!/bin/sh

branchName=`git rev-parse --abbrev-ref HEAD`
curl -s -X POST -H 'Content-type: application/json' --data '{"text":"ProjektName - Checkout: '$branchName'"}' https://hooks.slack.com/services/xxx/yyy/zzz >/dev/null 2>&1
```

### .git/hooks/post-commit

```
#!/bin/sh

branchName=`git rev-parse --abbrev-ref HEAD`
curl -s -X POST -H 'Content-type: application/json' --data '{"text":"ProjektName - Commit: '$branchName'"}' https://hooks.slack.com/services/xxx/yyy/zzz >/dev/null 2>&1
```
