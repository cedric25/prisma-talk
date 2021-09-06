## Some tests?

<div class="mt-8"></div>
<mdi-numeric-1-box class="inline text-orange-300 text-2xl -mt-1" />
By completely mocking Prisma client.

<div class="text-sm mt-2 ml-8">
👉 &nbsp;
<a href="https://www.prisma.io/docs/guides/testing/unit-testing" target="_blank">
https://www.prisma.io/docs/guides/testing/unit-testing
</a>
</div>

<div class="mt-12"></div>

<mdi-numeric-2-box class="inline text-orange-300 text-2xl -mt-1" />
By using a test database.

<div class="text-sm mt-2 ml-8 mb-4">
👉 &nbsp;
<a href="https://www.prisma.io/docs/guides/testing/integration-testing" target="_blank">
https://www.prisma.io/docs/guides/testing/integration-testing
</a>
</div>

 - Set your test database URL:

`DATABASE_URL=postgresql://test-user:plop@localhost:5432/freely-test`

 - Clean all tables between each test.

`TRUNCATE TABLE \"${dbSchemaName}\".\"${tablename}\" CASCADE;`

More info <a href="https://www.prisma.io/docs/concepts/components/prisma-client/crud#deleting-all-data-with-raw-sql--truncate" target="_blank">here</a>.
