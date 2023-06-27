# 🚩 Enabling/Disabling Features

To enable or disable certain features in the product, we leverage the use of database feature flags and cookies.

## Database Feature Flags

When we want to enable or disable a feature for all users, we need to use feature flags. We have a model named `Feature` that represents these flags that are persisted in the database. A migration needs to be written to modify the records in this table.

## Cookies

When we want to enable or disable a feature for a specific user, we instead will use cookies. This way, we can send users instructions on how to interact with select cookies. For example, to enable the new booker before it launched for everyone, we had the `api/newbooker/enable` route that returned a cookie with the key of `new-booker-enabled` allowing us to check that cookie on subsequent requests.
