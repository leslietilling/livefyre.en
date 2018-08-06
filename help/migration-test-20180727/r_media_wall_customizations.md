---
description: Change the size, width, and interaction options of the Media Wall app.
seo-description: Change the size, width, and interaction options of the Media Wall app.
seo-title: Media Wall Customizations
solution: Experience Manager
title: Media Wall Customizations
uuid: 9974cf65-4dba-4925-a68c-52a683dc5417
index: y
internal: n
snippet: y
translate: y
---

# Media Wall Customizations


<a id="section_onc_xtg_sy"></a>

Media Walls stream live images and other content into a real-time social wall, visualizing all activity surrounding an event.
If enabled, users may post text, images, or video directly to this App. Supported file types include 3GP, ASF, AVI, DV, GIF, JPG, MOV, MP4, MPEG, MPG, PNG, QT, and WMV Videos may be up to 25 MB.

* ** `Items to load` ** 
  Sets the initial number of content items displayed.

* ** `Load content with animation.` ** Turn on this option to load the Media Wall on a page with animation. Turn off this option to load the Media Wall on a page without animation.
* ** `Number of columns.` ** Set the number of columns for the Media Wall. The number of columns remains the same, regardless of the size of the window or browser. If you select Auto, the number of columns adjusts to display an optimized number of columns for the screen size.
* ** `Fit content to width` **. When this option is off, the content is cropped to a square. Toggle this option to on to display an entire image in the card, whether it fills up the entire card or not.

* ** `Include content modal` ** 
  Allows users to click on a photo in the stream to open it in an overlaid popup window.

* ** `Require rights` **. Enable this option to display only content with a rights request status of "Granted."
* ** `Hide social branding when rights granted` ** Switch this on to remove the logo for the originating social media network (Twitter or Instagram) when rights are granted for a piece of content.

* ** `Upload Button` ** 
    * ** `Allow user posts` **. Select whether you will allow users to post text, photo, or video with the upload button.

    * ** `Require Media` **. Toggle to on to require users to upload only photo or video content using the Upload Button.
    * You can edit the default text for the following Upload Button fields:
    
        * ** `Upload Button Text` **. Text for the Upload Button. Default text is "What’s on your mind?"
        * ** `Comment Modal Title` **. The title for the modal site visitors use to post content. Default text is "Post Your Comment."
        * ** `Comment Modal Button` **. The text of button site visitors click to post content. Default text is "Post Your Comment."



* ** `Call-to-action button` ** You can use the Call-to-action button with a product catalog to direct users to a product or to your site for further action.

    * ** `Call-to-action button` ** Switch the toggle to on to display the Call-to-action button.

    * ** `Require rights to display products` ** Switch the toggle to on to require that the content owner has granted rights for the content before a Call-to-action button appears for the content.

      >[!NOTE]
      >
      >The content displays even if rights are not granted for the content, but the Call-to-action button will not display with the content unless rights for the content are granted.

    * ** `Call-to-action header text` ** The words to display in the header above the Call-to-action button in the content modal. Default wording is, "Shop these products:".

    * ** `Call-to-action button text` ** The words to display in the Call-to-action button in the content modal. Default text is, "Buy Now:".

    * ** `Product display options` ** Choose whether you want to display the Photo and Product name with the Call-to-action button.

      >[!NOTE]
      >
      >Both the Photo and Product name buttons highlight blue when they are enabled.

    * ** `Product URL referral tracking` ** Switch the toggle to on to track referrals from this App to the associated product page.

    * ** `Referral tracking key-value pairs` ** Add parameters to further specify the referral tracking from your App content to the associated product page.


* ** `Product page filter` **.
    * ** `Filter UGC by Product ID` **. Select this option to create one App for multiple product pages. Filter product-specific UGC to the App for each product page. You can select one or more folders to associate specific collections to the App.
    * ** `Select Product folders` **. Select the top-level product folders to use to filter UGC. Use CTRL/Command + click to select more than one folder. Livefyre uses the folder to determine which products in that folder to display in the App on various pages.
    * ** `Show related content` **. Toggle this to display content published to the App, but tagged with a different product ID. After the product-specific content for the App displays, Livefyre displays content for other products and content not associated with a product. Livefyre prioritizes the content with the same product ID first, then content published to the App with other product IDs, then content published to the App with no product IDs.

You can customize Media Wall using:

* ** `Style` ** and ** `Config` ** options for all Apps in the ** `App Designer` **. See Customizing Apps for details on the standard ** `Style` ** and ** `Config` ** options for all Apps in the ** `App Designer` **.
* Integration tools. See [Media Wall Integration](c_media_wall_integration.md#c_media_wall_integration) for more on how to customize a Media Wall using Integration Tools.