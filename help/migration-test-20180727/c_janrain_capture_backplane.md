---
description: Janrain Capture and Backplane sends successful log in and log out messages that a Livefyre App can use.
seo-description: Janrain Capture and Backplane sends successful log in and log out messages that a Livefyre App can use.
seo-title: Janrain Capture/Backplane
title: Janrain Capture/Backplane
uuid: e380bba6-ccc4-469c-b61a-8bbb55820113
index: y
internal: n
snippet: y
translate: y
---

# Janrain Capture/Backplane

Janrain sends successful login/logout messages through the Backplane bus, on which the Livefyre App, when properly configured, listens. These messages contain all the information needed to show App users as logged in or logged out. Developers can view Backplane bus messages by inspecting the Network tab in your browser’s developer console.

## Login {#section_ftt_tvp_mz}

Request:

```
https://backplane1.janrainbackplane.com//bus/{CUSTOMER_NAME}/channel/{CHANNEL}?callback=Backplane.response&amp;rnd=0.15930617856793106
```
Response:

```
Backplane.response([{ 
  "id": "2014-05-06T22:51:55.406Z-eZp1HB1F7B", 
  "channel_name": "{CHANNEL_NAME}", 
  "message": { 
    "source": "http://{CUSTOMER_DOMAIN}", 
    "type": "identity/login", 
    "sticky": true, 
    "payload": { 
      "context": "http://{CUSTOMER_DOMAIN}", 
      "identities": { 
        "startIndex": 0, 
        "itemsPerPage": 1, 
        "totalResults": 1, 
        "entry": { 
          "id": "https://{CUSTOMER}.janraincapture.com/oauth/public_profile?uuid={UNIQUE_USER_ID}", 
          "displayName": "{USER_DISPLAY_NAME}", 
          "accounts": [ 
            { 
              "username": "{USER_DISPLAY_NAME}", 
              "identityUrl": "https://{CUSTOMER}.janraincapture.com/oauth/public_profile?uuid={UNIQUE_USER_ID}", 
              "photos": [ 
                { 
                  "id": 48570146, 
                  "value": "https://lh3.googleusercontent.com/-h8poqH8hlgw/AAA/AAA1/QuHtbeHMJzc/photo.jpg?sz=50", 
                  "type": "other" 
                }, 
                { 
                  "id": 48570147, 
                  "value": "https://lh3.googleusercontent.com/-h8poqH8hlgw/AAA/AAA1/QuHtbeHMJzc/photo.jpg?sz=50", 
                  "type": "original" 
                }, 
                { 
                  "id": 48570148, 
                  "value": "https://lh3.googleusercontent.com/-h8poqH8hlgw/AAA/AAA1/QuHtbeHMJzc/photo.jpg?sz=50", 
                  "type": "large" 
                }, 
                { 
                  "value": "https://lh3.googleusercontent.com/-h8poqH8hlgw/AAA/AAA1/QuHtbeHMJzc/photo.jpg?sz=50", 
                  "type": "avatar" 
                } 
              ] 
            }, 
            { 
              "identityUrl": "{USER_PROFILE_LINK}" 
            } 
          ] 
        } 
      } 
    } 
  } 
} 
]);
```
Empty Response:

```
Backplane.response([]);
```

## Logout {#section_t52_svp_mz}

Request:

```
https://backplane1.janrainbackplane.com/v1.2/bus/{CUSTOMER}/channel/new?callback=Backplane.finishInit&amp;amp;rnd=0.1057701709214598
```
Response:

```
Backplane.finishInit("{CHANNEL}");
```
If these messages are not appearing in your network requests, Livefyre will not be aware of the login/logout attempts and therefore, Livefyre won’t be able to integrate the user into the App.

## Integrate Livefyre with Janrain Capture or Backplane {#section_wng_zwt_bbb}

You can use Janrain Capture and Backplane with Livefyre Auth to allow users to engage with your Livefyre Apps when they log in to your site.
Skip this section if you’re not using Janrain Capture.
Customers using Janrain Capture and Backplane can use Livefyre Auth for Single Sign On (SSO), allowing users to immediately engage with your Livefyre Apps when they log in to your site. To benefit from this built-in Capture/Backplane integration, you must make configuration changes to both your Capture app and your Livefyre.js integration.
For more information, see [ Janrain’s Backplane documentation ](http://developers.janrain.com/how-to/integrations/self-serve-integrations-and-tools/backplane-1-2/).

1. Set Up Capture.
1. (Optional) Add Livefyre Defaults to your Capture App.
1. Build the AuthDelegate Object.
1. Sync to Livefyre with Ping for Pull.

## Set Up a Janrain Capture App {#section_r2f_kxt_bbb}

Livefyre needs certain credentials from your Janrain Capture app.

1. Set up the Janrain Capture app.
1. Enter the following information for Livefyre: 
    * Access to your Janrain Capture instance.
    * Access to your Janrain Engage dashboard.
    * Your Capture settings and credentials.
    * Your Engage credentials.
    * Your identity URL.


>[!NOTE]
>
>Livefyre receives data directly from the CNAME; therefore, this identity URL cannot be a CNAMEd record (a vanity URL CNAME) that resolves to the Janrain Capture’s actual CNAME.


## Add Livefyre Defaults to your Capture App {#section_z2s_txt_bbb}

Add Livefyre defaults to users stored in your Capture app to enable you to send users email notifications or allow them to automatically follow conversations that users comment on.

1. Set up the Capture App.
1. Add the following Livefyre default fields. All fields are optional.

|  Parameter  | Type  | Description  |
|---|---|---|
|  ** ` livefyre_comments` ** | String  | Notify user when someone comments on an article that they’re following. Can be immediately, often, or never.  |
|  ** ` livefyre_likes` ** | String  | Notify user when someone likes one of their posts. Can be immediately, often, or never.  |
|  ** ` livefyre_replies` ** | String  | Notify user when someone replies to one of their posts.Can be immediately, often, or never.  |
|  ** ` livefyre_moderator_comments` ** | String  | Notify moderator when someone comments on a conversation that they’re moderating.Can be immediately, often, or never.  |
|  ** ` livefyre_moderator_flags` ** | String  | Notify moderator when someone flags a post on a conversation that they’re moderating.Can be immediately, often, or never.  |
|  ** ` livefyre_autofollow_conversations` ** | Boolean  | Have the user auto-follow a conversation when they leave a post. Can be true or false.  |


## Connecting Janrain to Livefyre using AuthDelegate {#section_asv_vyt_bbb}

Livefyre.require provides a plugin that enables auth to listen to the Janrain Backplane bus.
When an identity/login message is broadcast on the Backplane channel, auth.authenticate() will be called for you with the user’s Livefyre Authentication token. You must still implement an AuthDelegate.

```
Livefyre.require(['auth', 'backplane-auth-plugin#0'], function(auth, backplanePluginFactory) { 
   auth.plugin(backplanePluginFactory('network.fyre.co')); 
   auth.delegate({ 
      login: function (finishLogin) { 
         loginWithCapture(finishLogin); 
      } 
   }); 
});
```

>[!NOTE]
>
>The window.Backplane object must be defined on your page before calling auth.plugin with the Livefyre Backplane plugin. To make sure the Backplane object is available, call the Livefyre instantiation code from an onReady callback. Consult your Janrain contact to determine when other applications may use the Backplane object.

The following are some examples of how an auth delegate may look for a Janrain Capture integration.

>[!NOTE]
>
>Your auth delegate will vary depending upon your Janrain instance.


* 

    * The callback passed to your auth delegate’s login method
    * The reference to your Janrain capture variable.
    * : A reference to your Backplane object.


```
/** 
* Login function 
* In this case, opens a login modal and triggers Backplane to start listening 
* for login messages 
*/ 
authDelegate.login = function(finishLogin) { 
   var successCallback = function() { 
      // These need to be replaced with the actions that correspond to successful login  
      // and when the Janrain modal is closed. 
      janrain.events.onCaptureLoginSuccess.removeHandler(successCallback); 
      janrain.events.onModalClose.removeHandler(failureCallback); 
      finishLogin(); 
   }; 
  
   var failureCallback = function(e) { 
      janrain.events.onModalClose.removeHandler(failureCallback); 
      janrain.events.onCaptureLoginSuccess.removeHandler(successCallback); 
      finishLogin(e || new Error("Error logging in with Janrain Capture")); 
   }; 
  
   // Open the modal to log a user in 
   janrain.capture.ui.renderScreen('signIn'); 
   // Send a backplane message 
   window.Backplane.expectMessages('identity/login'); 
   // Add handlers to specific janrain events 
   janrain.events.onCaptureLoginSuccess.addHandler(successCallback); 
   janrain.events.onModalClose.addHandler(failureCallback); 
};
```
Logout

```
/** 
* Logout function 
* In this case, invalidates the session and removes the cookie. 
* Also reloads the page to change state. In order to do this without a reload, 
* it would be necessary to also update the UI. 
*/ 
authDelegate.logout = function(finishLogout) { 
   Backplane.resetCookieChannel(); 
   janrain.capture.ui.endCaptureSession(); 
   finishLogout(); 
}; 

```
Edit Profile
This can link to whatever part of the site you would like users to visit to view their own profile page. This example merely prints out the author object passed in.

```
/** 
* Edit profile function 
* @param user - User who would like to edit their profile 
*/ 
authDelegate.editProfile = function(user) { 
   console.log(user); 
}; 

```
View Profile
Like Edit Profile, this should link to a user’s page that is different from the currently logged in user. This can be implemented however you see fit. This example simply logs the author parameter to the console.

```
/** 
* View profile function 
* @param user - User or userId whose profile should be displayed 
*/ 
authDelegate.viewProfile = function(user) { 
   console.log(author); 
};
```

## Sync to Livefyre with Ping for Pull {#section_ilv_bzt_bbb}

**Step 4: Sync to Livefyre with Ping for Pull**
Keeping Livefyre Remote Profiles in sync with your Capture user management system involves a series of steps referred to as Ping for Pull. This process requires that you obtain a valid access token from Janrain, and then pass that token to an endpoint specified in step 3, below.

1. Get an access code from Janrain.
   To get the access code, supply the necessary credentials, specify the user_type as “user”, and the uuid as the current user’s uuid to update. For more information, see [ http://developers.janrain.com/rest-api/methods/authentication/access-codes-and-tokens/getauthorizationcode/. ](http://developers.janrain.com/rest-api/methods/authentication/access-codes-and-tokens/getauthorizationcode/)

1. Trade the access code for an access token. Supply the necessary credentials, the access code received from step 1, and specify the grant_type as “authorization_code”.
   For more information, see [ http://developers.janrain.com/rest-api/methods/authentication/oauth/token/ ](http://developers.janrain.com/rest-api/methods/authentication/oauth/token/)

1. Hit the Livefyre “Ping to Pull Capture” endpoint.
   Endpoint URL: ` http://{networkName}/api/v1.1/private/capture/profile_updated/?jrtoken={token}` where ***{networkName}*** is the network name provided to you by Livefyre, and the jrtoken is the token received from Janrain in step 2. 
   Once you hit this endpoint, you receive a 202 response and Livefyre begins an async process.
