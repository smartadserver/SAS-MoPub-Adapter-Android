Smart AdServer - MoPub SDK Adapter for Android
==============================================

This repository is deprecated, please refer to the new repository https://github.com/smartadserver/smart-mopub-mediation-adapter-android.

Introduction
------------
The **_Smart AdServer Android SDK_** can be used with **_MoPub SDK_** through Custom Event Classes provided in this repository.
Supported Ad Formats are _Banners_, _Fullscreen_, _Rewarded Video_ and _Native Ads_.

Setup
-----

1) Install the **_Smart AdServer Android SDK_** in your Android Studio Project. You can follow the instructions in our [documentation](http://help.smartadserver.com/Android/V6.6/#IntegrationGuides/InstallationGuide.htm).


2) Checkout this repository and merge the src/ folder (containing adapter classes) into the src/ folder of your project. Folder structure should be as follows :
com/smartadserver/android/library/mediation for all custom event (banner, interstitial, rewarded video, native) and utility classes.
com/mopub/nativeads for the specific MoPub renderer class for native ads with video content


4) _(Optional)_ **If you plan to use Native Ads with video, you need to register _`SASNativeVideoAdRenderer`_ as a MoPubRenderer for mediated Smart AdServer native ads with video. More info on MoPub [documentation](http://www.mopub.com/resources/docs/android-sdk-integration/integrating-native-ads-android/).  **


5) On your MoPub's dashboard, create a new ***Custom Native Network*** under the _Networks_ tab, and fill your Ad Units with the relevant Custom Event Classes. _For example for a banner Ad Unit, set `SASMoPubCustomEventBanner` as the **Custom Event Class**_.


6) Fill the _**Custom Event Class Data**_ with the informations of your _Smart AdServer's_ placements. You must use a valid JSON String and the 4 parameters : **siteid**, **pageid**, **formatid** and **target** must exist in this string. If you want to leave a parameter empty (_target for instance_) feel free to do it, as long as **all keys exist**.
  ```
  {"siteid":"your-siteID","pageid":"your-pageID","formatid":"your-formatID","target":"your-target-or-empty"}
  ```


7) Make sure your new _Custom Native Network_ is activated for your chosen Ad Units and Segments.


8) That's it, you're all set, you should be able to display _Smart AdServer's_ ads through your _MoPub SDK_ integration.

Known limitations
----------
- **Impressions** : due to a different logic in impression counting, you may experience discrepancies between MoPub and Smart AdServer impression statistics for Interstitial and RewardedVideo placements. MoPub will count impressions only when the ad is shown whereas Smart AdServer will count as soon as the ad is fully loaded even if you never display it. 


More infos
----------
You can find more informations about the _Smart AdServer Android SDK_ and the _MoPub SDK Custom Events_ in the official documentation: http://help.smartadserver.com/en/
