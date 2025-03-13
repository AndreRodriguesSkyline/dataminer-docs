---
uid: STaaS_features
---

# STaaS features

## Data location and redundancy

DataMiner STaaS relies on Azure Storage, which stores multiple copies of your data to make sure it is always available even in case outages or disasters occur. Different storage redundancy setups are possible. STaaS supports zone-redundant storage and geo-redundant storage. When you contact Skyline to register your system to use STaaS, you can include your preferences as to the region(s) where your data should be stored and the type of storage redundancy that should be used.

> [!NOTE]
> DataMiner STaaS's standard supported regions are West Europe (The Netherlands), UK South, North Central US, UAE North, Southeast Asia (Singapore), and Australia East. Choosing regions outside this standard list will incur additional charges.

- **Zone-redundant storage (ZRS)** copies your data synchronously across three Azure availability zones in one region. Each availability zone is a separate physical location with independent power, cooling, and networking. By **default**, DataMiner STaaS uses ZRS.

- **Geo-redundant storage (GRS)** copies your data synchronously three times within a single physical location in the primary region and then also copies your data asynchronously to a single physical location in the secondary region. Only specific regions can be combined in such a setup, e.g. if the primary region is Switzerland North, the secondary region can only be Switzerland West. For an overview of the supported regions, see [Azure paired regions](https://learn.microsoft.com/en-us/azure/reliability/cross-region-replication-azure#azure-paired-regions). GRS is **available upon request**, but will result in additional charges. If you wish to use DataMiner STaaS with GRS, contact <staas@dataminer.services>.

> [!TIP]
> For detailed information, see [Azure Storage redundancy on learn.microsoft.com](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy)

## Data resilience and backups

To ensure data resilience for potential recovery scenarios, protecting against user errors and accidental changes, your data is backed up with a **granularity of 1 day**. Backups are stored for **30 days**.

- **Daily backups**: STaaS performs backups with a granularity of 1 day and maintains a 30-day rolling snapshot of your data.

- **Data restoration and support**: In the event a rollback is necessary, our support team will assist you. To submit a rollback request, contact the support team by sending an email to <staas@dataminer.services>. They will guide you through the necessary steps to ensure a successful data restoration.

> [!IMPORTANT]
> When you [disconnect a system from dataminer.services](xref:Disconnecting_from_dataminer.services#permanently-disconnecting-from-dataminerservices) or [remove a DaaS system](xref:Removing_a_DaaS_system), all STaaS data for that specific system, including backups, will be removed 7 days after you take this action. Upon request, all STaaS data can be recovered within those 7 days.

## Data security and availability

With STaaS, the data for a specific DMS is isolated in a logical partition. You can only ever access the logical partition dedicated to your own DMS, and all partitions are strictly isolated from each other.

To access your data, you use a connection authenticated with a [Service Principal](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?tabs=browser#service-principal-object). With this connection, you can only access the logical partition dedicated to a specific DMS, which means that all data of a DMS is strictly isolated.

The data is encrypted both at rest and in transit.

If [ZRS](#data-location-and-redundancy) is used, STaaS has an expected availability of 99.90%. With [GRS](#data-location-and-redundancy), it has an expected availability of 99.95%. For more information, please contact <sales@skyline.be>.

## TTL

It is not yet possible to configure time-to-live (TTL) values for STaaS. In the table below, you can find the default TTL values for each data type.

| Data type                | TTL          |
|--------------------------|:------------:|
| Real-time trending       | 7 days       |
| Average trending (short) | 3 months     |
| Average trending (medium)| 2 years      |
| Average trending (long)  | 10 years     |
| State changes            | 5 years      |
| Spectrum traces          | 1 year       |
| Alarm events             | 1 year       |

## Limitations

To **migrate existing data** to STaaS, the following limitations apply:

- Migration is supported from DataMiner 10.4.0 [CU2]/10.4.5 onwards.<!-- RN 38884 -->

- Migration of a setup with multiple OpenSearch/Elasticsearch clusters is not yet supported.

- Migration from a MySQL setup is not yet supported.

- Migration using a proxy is supported from DataMiner 10.4.6 onwards<!-- RN 39313 -->.

- If you start the migration while an element with a logger table is stopped, the data of that element will not be migrated.

In addition, the following **other limitations** currently apply:

- [Jobs](xref:jobs), [Ticketing](xref:ticketing), and [API Deployment](xref:Overview_of_Soft_Launch_Options#apideployment) data are not supported.

- The following indexing engine functionality is not supported: Alarm Console search tab, search suggestions in the Alarm Console, aliases, and aggregation.

- Custom configuration of TTL values is not yet supported.

- Direct queries from DataMiner Cube to the database are not supported.

- The [SLReset tool](xref:Factory_reset_tool) is not supported.

- [Exporting trend data](xref:Exporting_elements_services_etc_to_a_dmimport_file) to a .dmimport file is not supported.

- DMZ setups are currently not supported.

- Adding a DataMiner Agent to a DMS using STaaS requires [additional manual configuration steps](xref:Adding_a_DMA_to_a_DMS_running_STaaS).

- Regarding logger tables:

  - The [autoincrement](xref:Protocol.Params.Param.ArrayOptions.ColumnOption-type#autoincrement) tag is not supported.

  - [Indexed logger tables](xref:AdvancedLoggerTablesImplementation#indexed-logger-tables) can be created and read from the database, but advanced search queries with GQI are not supported.

  - [DirectConnection logger tables](xref:AdvancedLoggerTablesDefiningDirectConnectionTable) are not supported.
