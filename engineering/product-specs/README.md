---
description: A place for questions about very specific queries about the Product
---

# 📃 Product Specs

* Calendars
  * A user can connect multiple google calendars at a time, but only one calendar would be used at a time to create the invites which can be globally changed in Calendar settings(Installed Apps)
  * Availability will be checked across all available calendars.
  * When a booking is done(normal/reschedule), all integrations(Calendar, Webhooks) are first updated and then DB is updated. Note that failures in Calendar updates still let DB update which is intentional.
* Bookings
  * 10 bookings are fetched at a time in the infinite loader of bookings.
