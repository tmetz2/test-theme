---
layout: page
title: Changing membership visibility through the API
description: Changing organization membership using the API when the UI times out.
author: jaymeperlman
last_updated: 2020-11-20
owner_slack: support-docs
owner_team: support-docs
owner_repo: support-docs-content 
toc: true
---

Members of a very large organization (50,000+ members), such as EpicGames, may run into timeout issues when managing their membership visibility. If this happens, they can use the GitHub REST API instead.  You can send them one of the canned replies from below.

## Product and version

This doc applies to:

| Product| Version|
|---|---|
|  Free, Pro, Team     | Latest         |



## Making membership public

Unfortunately the \`EpicGames\` organization has so many members that it is prone to timeouts, and we can't load a complete member list in the web interface. We do, however, offer an API end point for this: 

https://docs.github.com/en/rest/reference/orgs#set-public-organization-membership-for-the-authenticated-user

Just some quick house keeping before looking at the request. If you are new to our API, I'd recommend taking a read through our API docs:

https://docs.github.com/en/free-pro-team@latest/rest
https://docs.github.com/en/free-pro-team@latest/rest/guides

Next, you'll want to understand how to make an authenticated request:

https://docs.github.com/en/free-pro-team@latest/rest/overview/resources-in-the-rest-api#authentication
https://docs.github.com/en/free-pro-team@latest/rest/overview/other-authentication-methods

And create a personal access token:

https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

When determining the scopes you need when creating a token we have this great list:

https://docs.github.com/en/free-pro-team@latest/developers/apps/scopes-for-oauth-apps

For this example we'll be using a personal access token:

\`\`\`

curl  -X PUT \
-H "Accept: application/vnd.github.v3+json" \
-H "Authorization: token :token" \
-H "Content-Length: 0" \
https://api.github.com/orgs/EpicGames/public_members/:username

\`\`\`

You'll have to replace the \`:token\` with your personal access token mentioned earlier, and \`:username\` with your GitHub username.

If this fails, please could you provide full output of a curl -v request that demonstrates this? (-v for verbose logging)

http://curl.haxx.se/

That should help us investigate the issue. Also, please make sure you mask any sensitive information like OAuth tokens and Authorization headers in the output of the curl command.


## Making membership visibility private

Unfortunately the \`EpicGames\` organization has so many members that it is prone to timeouts, and we can't load a complete member list in the web interface. We do, however, offer an API end point for this: 

https://docs.github.com/en/rest/reference/orgs#set-public-organization-membership-for-the-authenticated-user

Just some quick house keeping before looking at the request. If you are new to our API, I'd recommend taking a read through our API docs:

https://docs.github.com/en/free-pro-team@latest/rest
https://docs.github.com/en/free-pro-team@latest/rest/guides

Next, you'll want to understand how to make an authenticated request:

https://docs.github.com/en/free-pro-team@latest/rest/overview/resources-in-the-rest-api#authentication
https://docs.github.com/en/free-pro-team@latest/rest/overview/other-authentication-methods

And create a personal access token:

https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

When determining the scopes you need when creating a token we have this great list:

https://docs.github.com/en/free-pro-team@latest/developers/apps/scopes-for-oauth-apps

For this example we'll be using a personal access token:

\`\`\`

curl  -X DELETE \
-H "Accept: application/vnd.github.v3+json" \
-H "Authorization: token :token" \
https://api.github.com/orgs/EpicGames/public_members/:username

\`\`\`

You'll have to replace the \`:token\` with your personal access token mentioned earlier, and \`:username\` with your GitHub username.

If this fails, please could you provide full output of a curl -v request that demonstrates this? (-v for verbose logging)

http://curl.haxx.se/

That should help us investigate the issue. Also, please make sure you mask any sensitive information like OAuth tokens and Authorization headers in the output of the curl command.

### Troubleshooting

If this call fails, have the user run the following `cURL -v` request _(`-v` for verbose logging)_ and provide us with the full output to help us investigate the issue. Make sure the user masks or removes any sensitive information like OAuth tokens and Authorization headers.

```curl
http://curl.haxx.se/
```

## Prior Art

- [Example ticket](https://github.zendesk.com/agent/tickets/427409)
