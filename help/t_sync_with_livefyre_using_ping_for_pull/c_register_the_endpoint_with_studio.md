---
description: Register the URL endpoint so Livefyre can use the URL to pull updated profile information.
seo-description: Register the URL endpoint so Livefyre can use the URL to pull updated profile information.
seo-title: Register the Endpoint with Studio
solution: Experience Manager
title: Register the Endpoint with Studio
uuid: ae18bd02-e0f2-4ecb-8329-9cb710acee20
index: y
internal: n
snippet: y
translate: y
---

# Register the Endpoint with Studio

Register the Ping for Pull URL only once per network. Once set, this value should not change unless the endpoint for fetching user profile data from your user management system changes.

1. Use Studio to register this URL endpoint with Livefyre.
1. Register the URL from which Livefyre will fetch updated user profile information, go to **[!UICONTROL  Studio > Settings > Integration Settings > Remote Profiles]**, and enter it in the **[!UICONTROL  Ping for Pull URL]** field.

   For example, the URL can look like: https://example.yoursite.com/some_path/?id={id}
