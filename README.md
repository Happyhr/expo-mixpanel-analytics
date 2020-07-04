Expo Mixpanel Analytics
=========

Mixpanel integration for use with React Native apps built on Expo or Ejected to Expokit.

## Installation

```
npm install --save @aayushgarg14/expo-mixpanel-analytics
```

## Import

Your React Native app's screen resolution, app name, app ID, app version, device information and multiple other parameters will be automatically resolved and sent with each event.
```
import ExpoMixpanelAnalytics from '@aayushgarg14/expo-mixpanel-analytics';
```

## Usage
```js

const analytics = new ExpoMixpanelAnalytics(MIXPANEL_TOKEN);

// Called when the user signs up. This will create an alias from the unique Id provided, for the user profile.
analytics.alias(UNIQUE_ID);

// Called when the user logs in to associate with the alias profile already created. This helps if the user logs in from another device.
analytics.identify(UNIQUE_ID);

// Track events with parameters ( optional ) send as second argument.
analytics.track("Event Name", { "Referred By": "Friend" });

// Set and update the people (user) property.
// !Important: People update will not be sent to Mixpanel until user is identified via alias or identity call.
analytics.people_set({ "$first_name": "Joe", "$last_name": "Doe", "$email": "joe.doe@example.com", "$created": "2013-04-01T13:20:00", "$phone": "4805551212", "Address": "1313 Mockingbird Lane", "Birthday": "1948-01-01" });


// Set the people property that you don't want to be overwritten.
// !Important: People update will not be sent to Mixpanel until user is identified via alias or identity call.
analytics.people_set_once({ "First login date": "2013-04-01T13:20:00" });

analytics.people_unset([ "Days Overdue" ]);

// This adds 12 to a running total of Coins Gathered for people property
analytics.people_increment({ "Coins Gathered": 12 });

analytics.people_append({ "Power Ups": "Bubble Lead" });

analytics.people_union({ "Items purchased": ["socks", "shirts"] });

analytics.people_delete_user();

analytics.reset();

```

## References
https://mixpanel.com/help/reference/http