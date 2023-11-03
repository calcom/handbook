# Disallowing the use of unrestricted Metadata fields

#### WHY?

PostgreSQL has long been esteemed for its robustness and its ability to handle a wide variety of data types, including JSON. JSON support in PostgreSQL allows for a non-relational representation of data structures, providing flexibility in how data is stored and retrieved. However, while there are scenarios where JSON is beneficial, certain limitations exist that can make its use in PostgreSQL disadvantageous.

Opting to use JSON because it's "easy" is akin to just spinning up a MongoDB cluster to store data we are not caring about enough to restrict with a specific schema.

#### PERFORMANCE DRAWBACKS

JSON data is not stored in a pre-defined manner, which can lead to significant performance overhead. The database engine must parse JSON data for each query, which can be computationally expensive, leading to slower query performance compared to traditional relational data storage. This is particularly noticeable in large-scale databases or when executing complex queries that require the database to sift through sizable JSON documents.

#### INDEXING DIFFICULTIES

While PostgreSQL does allow for indexing JSON data, these indexes are typically not as efficient as those on traditional column data. Indexing a JSON field requires the creation of a functional index on the specific key within the JSON blob, which can lead to a proliferation of indexes and increased maintenance overhead. Furthermore, these indexes can be less performant, especially if the queries are not well-aligned with the index structure.

#### DATA MODIFICATION

Modifying data within a JSON field can be cumbersome. Unlike standard fields that can be updated directly using SQL 'UPDATE' statements, changing a single value within a JSON document often requires rewriting the entire document. This can lead to inefficient data manipulation operations, particularly for larger JSON documents.

{% hint style="info" %}
#### HOW TO SOLVE THIS?

In most cases, we're using metadata to store responses from third party APIs, e.g. Google Calendar, Stripe, etc. For most of these we're already defining a zod schema to parse said responses, thus, why not create columns or tables directly for those responses? We're getting type safety by the generated Prisma types, and we can index those fields (eg stripeCustomerId, which is currently living under the `metadata` within a User's object)
{% endhint %}

####
