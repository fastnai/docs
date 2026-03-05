---
description: >-
  Fastn gives users the ability to either connect their flows to their
  externally managed databases or to the fastn DB available on the platform.
---

# Connecting External Databases

## How to Connect to an External Database

You can connect to external databases in Fastn using **database connectors**. These allow you to run SQL queries within your flows or interact directly with external databases.

### **Ways to Add a Database Connector**

There are two primary ways to add a database connection:

1. **From Within a Flow**
   * While building a flow, drag in a **Connector** element.
   * Select the **Database** option.
   * Choose an existing database or click to add a new one.
2. **From the Databases Page**
   * Navigate to the **Databases** page using the left sidebar.
   * Click **Add New Database**.
   * Select the type of database you'd like to connect to (e.g., PostgreSQL, MySQL, Fastn DB, etc.).



<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfFDQ92XdO2VwamznZ7woxwQ43jEZ39uWCDwJvH5DecjHYZ00z6FWMB9DPJ2rSeoyUrpovj7NGaV0I-wI38zlXGW12n2E34Emv2TtJumbKZpV5LE6p0Y0FeOjLZLlQOWipcgOV5ew?key=aWFNWdC9I0x6b7wkwYQbDg" alt=""><figcaption></figcaption></figure>

### **Setting Up the Connection**

Once you've chosen the database type:

* Fill in the required configuration fields (e.g., host, port, username, password, database name).
* Click **Save** to finalize the connection.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcl-C3AwhQhnnG1KNQ0CcIeUfoLu2LFHiu8SgcpmNhUDrlwsO_KqUHzmDQq08uvcw8JmJthkoFd_pUvpTZbhbnsc1q0LfdcVqXJCva2_aGdWwsI41GW0d3TiEngSlAthpM7VicAJg?key=aWFNWdC9I0x6b7wkwYQbDg" alt=""><figcaption></figcaption></figure>

---

## Related topics

* [Connect to the Fastn DB](connect-to-the-fastn-db.md) — use Fastn's built-in database instead of an external one
* [Database (Flow Component)](../designing-a-flow/database.md) — add SQL queries as flow steps to interact with your databases
* [Managing & Using Connectors](../connecting-apps/managing-and-using-connectors.md) — create custom database connectors for your workspace
* [Setting Up a Redshift to GCS Migration Flow](../../../resources/library/tutorials/data-migrations/setting-up-a-redshift-to-gcs-migration-flow.md) — tutorial using an external Redshift database in a migration flow
