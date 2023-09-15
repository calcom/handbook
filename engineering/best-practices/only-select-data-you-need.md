# Only select data you need

1\) Increased performance overhead: When you select all columns from a table, Prisma retrieves all the data associated with each row, which can result in a significant performance impact. This includes reading unnecessary columns and transferring a large volume of data between your application and the database.

2\) Unnecessary data exposure: Selecting all columns exposes sensitive data that might not be required by your application. This can pose security risks, especially if the table contains sensitive user information or proprietary data. (In our case app credentials and booking information)

&#x20;![](<../../.gitbook/assets/ray-so-export (5).png>)
