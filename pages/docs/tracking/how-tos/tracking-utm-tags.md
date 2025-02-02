# Tracking UTM Tags


When setting up your Mixpanel implementation, one issue of particular interest is tracking users by their original source of traffic. By default, Mixpanel does some of this tracking for you on the web in the form of several [default properties](/docs/tracking/reference/default-properties).

## Web Attribution

### UTM Properties
Mixpanel's Javascript library tracks all [UTM tags](/docs/tracking/reference/javascript#tracking-utm-parameters) by default. This allows you to segment key actions by relevant campaign information using [attribution models](/docs/analysis/advanced/attribution), so that you can quantify the effectiveness of specific campaigns.

Mixpanel's Javascript library will also track initial_utm_parameters as a profile property, based on the first ever visit. This is helpful as if a user makes a purchase or completes some other important event, it is important to know want to know what acquisition channel brought them to your site originally.

### Initial Referrer and Initial Referring Domain Properties
Mixpanel's Javascript library will track Initial Referrer and Initial Referring Domain and append them as a property to any event that a user completes. These properties are stored in the Mixpanel cookie the first time a user comes to your site and will not change on future site visits as long as the cookie is not cleared.

If a user comes to your site from www.google.com for the first time, for example, then the initial referring domain is equal to www.google.com and the initial referrer is the URL that they first came from. This information will be stored in the Mixpanel cookie and sent with all future events.

Having this information allows you to build reports to see how users from different initial referrers convert through an application.

#### $direct
An initial referrer is equal to $direct when a user first lands on a site without being referred by another website. The user may have typed the website address directly, clicked a bookmark, clicked a link from an email, or might have security settings in their browser that prevent referrer data from being passed.

## Mobile Attribution
Mobile attribution, or tracking campaign source for app installs on iOS/Android, can be more complex than the web due to the way mobile devices store attribution information.

For Android, Google provides a [Play Install Referrer Library](https://developer.android.com/google/play/installreferrer/library) so you know where your installations came from. You can use the [getInstallReferrer ( )](https://developer.android.com/reference/com/android/installreferrer/api/ReferrerDetails#getinstallreferrer) method to retrieve the referrer URL string, parse it and send that data to Mixpanel as properties in events.

For iOS, users enter the Apple App Store carrying data about where they came from, but the App Store strips that data once the user arrives in the store. Therefore, users who download your application don’t come with any data showing where they were before arriving at the App Store.

In order to track channel attribution on iOS, you'll need to use a mobile attribution tool. You can see a list of the partners we integrate with on our [tech partners page](https://mixpanel.com/partners/integrations?categories=attribution-deep-linking).

## Server-Side Attribution
Unlike web tracking, server-side implementations generally don't have access to global contexts or variables that can provide attribution data. This means these data such as UTM parameters and referrer information need to be extracted manually from the request. See our [Effective Server-Side Tracking page on tracking attribution](/docs/tracking/how-tos/effective-server#tracking-attribution-from-utms-and-referer) for examples of how this could be done.
