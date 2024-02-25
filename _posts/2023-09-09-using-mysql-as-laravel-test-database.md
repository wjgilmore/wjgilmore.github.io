---
layout: post
title: "Using MySQL as the Laravel Test Database"
published: false
---

Open `phpunit.xml` and look for this `<php>` block:

```
<php>
    <env name="APP_ENV" value="testing"/>
    <env name="BCRYPT_ROUNDS" value="4"/>
    <env name="CACHE_DRIVER" value="array"/>
    <!-- <env name="DB_CONNECTION" value="sqlite"/> -->
    <!-- <env name="DB_DATABASE" value=":memory:"/> -->
    <env name="MAIL_MAILER" value="array"/>
    <env name="QUEUE_CONNECTION" value="sync"/>
    <env name="SESSION_DRIVER" value="array"/>
    <env name="TELESCOPE_ENABLED" value="false"/>
</php>
```

Note the two commented out `DB_*` declarations. This is pretty misleading in that (at least to me) it indicates that no database is configured for housing test data created during a test run. Not so! Lacking a declaration, Laravel will use the database defined within the `.env` file, wiping out any data found in that database in the process! Despite the best practice being to use seed files for easily creating realistic data for use within the development database, I have no doubt this behavior will enrage more than a few unsuspecting fellow developers once they realize their painstakingly created development data has disappeared. To fix this issue and use a _different_ MySQL database for the test environment, replace those two commented out lines with:

```
<env name="DB_CONNECTION" value="mysql"/>
<env name="DB_HOST" value="localhost"/>
<env name="DB_DATABASE" value="your_test_database_name"/>
<env name="DB_USERNAME" value="test_user" />
<env name="DB_PASSWORD" value="test_password" />
```
