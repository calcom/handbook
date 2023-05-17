---
description: Describes technical specs of App Store and behaviour of Apps available in it.
---

# 🏪 App Store

### Persistence-based categorization of Apps

In terms of the ways the apps store their data, apps can currently be categorized in following ways:

* Has data specific to the user **- **_**UserApp**_
  * Data can simply be credentials - **Simple**
    * Examples => Stripe with its credentials, Google Calendar with its credentials
    * Persistence =>  `Credentials` table in PG
  * Data can be more complex and structured in its own tables - **Complex**
    * Example - App decides its own schema, with the convention that the tables would be prefixed with _**`App_{CAMELCASED_APPID}_`**_ e.g. `App_RoutingForms_Form` and `App_RoutingForms_FormResponse`
* Has data specific to an EventType **- **_**EventTypeApp**_
  * Example =>  Rainbow, Giphy apps are configured per Event Type and thus every EventType can have its own data for that app.
  * Persistence => `EventType.metadata.apps.{APP_ID}` is where the app would store its key-value pairs



_Note: Even an EventType App can have its own user-level data e.g. Stripe App has EventType data as well as user-specific data in credentials._&#x20;

At the time being, every app no matter what has its entry in the `Credentials` table, atleast to mark that the app is installed.



### UserApps

* At the time, UserApps take care of miscellaneous enhancements
  * Calendar
  * Messaging
  * Video

### App Uninstallation

Almost all the apps can be uninstalled with the exception of the following 2 apps

* Cal Video
* Google Meet

When an App is uninstalled, the credential(from the `Credential` table) for that user is deleted.&#x20;

So, **SimpleUserApps** have their entire data deleted. So, e.g. Google Calendar on uninstallation and reinstallation would require a reconnect with Google(because credentials have been deleted)

_Video Apps, Calendar Apps and Stripe have special handling where they delete/reset their respective data as well which is stored in EventTypes._

* _Video Apps resets involved EventTypes location to **Cal Video**_
* _Stripe reset **price** to 0 and even hides the EventType_
* _Calendar Apps - (**Needs details**)_&#x20;

At the time of writing, **ComplexUserApps** don't have their complex data deleted. So, the RoutingForms app on uninstallation retains its forms and form responses. After re-installation user would be able to see that data back.

_We have plans to make it very clear during installation as to which data would be deleted._\




#### Further Readings

* [How to build an App in App Store](http://localhost:5000/s/vnsvL4GbkACtu7LWnJSR/how-to-guides/how-to-build-an-app)
