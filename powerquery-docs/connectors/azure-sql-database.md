---
title: Power Query Azure SQL database connector
description: Includes basic information and prerequisites, instructions on how to connect to your database, and information about advanced connection options.
author: bezhan-msft
ms.topic: conceptual
ms.date: 2/13/2023
ms.author: bezhan
---

# Azure SQL database

## Summary

| Item | Description |
| ------- | ------------|
|Release state | General Availability |
| Products supported | Power BI (Datasets)<br/>Power BI (Dataflows)<br/>Power Apps (Dataflows)<br/>Excel<br/>Dynamics 365 Customer Insights<br/>Analysis Services |
| Authentication types supported| Windows (Power BI Desktop, Excel, Power Query Online with gateway)<br/>Database (Power BI Desktop, Excel)<br/>Microsoft Account (all)<br/> Basic (Power Query Online) |
| Function reference docs | [Sql.Database](/powerquery-m/sql-database)<br/>[Sql.Databases](/powerquery-m/sql-databases) |

> [!NOTE]
> Some capabilities may be present in one product but not others due to deployment schedules and host-specific capabilities.

## Prerequisites

By default, Power BI installs an OLE DB driver for Azure SQL database. However, for optimal performance, we recommend that the customer installs the [SQL Server Native Client](/sql/relational-databases/native-client/applications/installing-sql-server-native-client) before using the Azure SQL database connector. SQL Server Native Client 11.0 and SQL Server Native Client 10.0 are both supported in the latest version.

## Capabilities supported

* Import
* DirectQuery (Power BI only)
* Advanced options
  * Command timeout in minutes
  * Native SQL statement
  * Relationship columns
  * Navigate using full hierarchy
  * SQL Server failover support

## Connect to Azure SQL database from Power Query Desktop

To connect to an Azure SQL database from Power Query Desktop, take the following steps:

1. Select the **Azure SQL database** option in the connector selection.

2. In **SQL Server database**, provide the name of the server and database (optional).

   ![Enter Azure SQL database connection.](./media/azure-sql-database/signin.png)

3. Select either the **Import** or **DirectQuery** data connectivity mode.

4. Optionally, you can select and enter advanced options that will modify the connection query, such as a command timeout or a native query (SQL statement). For information: [Connect using advance options](#connect-using-advanced-options)

5. Select **OK**.

6. If this is the first time you're connecting to this database, select the authentication type, input your credentials, and select the level to apply the authentication settings to. Then select **Connect**.

   ![Azure SQL database authentication.](./media/azure-sql-database/enter-credentials.png)

   For more information about authentication methods, go to [Authentication with a data source](../connectorauthentication.md).

   >[!Note]
   >  If the connection is not encrypted, you'll be prompted with the following message.

   ![Azure SQL database encryption support.](./media/azure-sql-database/encryption-warning.png)

   Select **OK** to connect to the database by using an unencrypted connection, or follow the instructions in [Enable encrypted connections to the Database Engine](/sql/database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine) to set up encrypted connections to Azure SQL database.

7. In **Navigator**, select the database information you want, then either select **Load** to load the data or **Transform Data** to continue transforming the data in Power Query Editor.

   ![Power Query Desktop Navigator showing the Human Resources employee data.](./media/azure-sql-database/navigator-desktop.png)

## Connect to Azure SQL database from Power Query Online

To connect to an Azure SQL database from Power Query Online, take the following steps:

1. Select the **Azure SQL database** option in the connector selection.

2. In **Azure SQL database**, provide the name of the server and database.

   ![Enter the Azure SQL database online connection.](./media/azure-sql-database/service-signin.png)

   You can also select and enter advanced options that will modify the connection query, such as a command timeout or a native query (SQL statement). More information: [Connect using advanced options](#connect-using-advanced-options)

3. If this is the first time you're connecting to this database, select the authentication kind and input your credentials.

4. If necessary, select the name of your on-premises data gateway.

5. If the connection is not encrypted, clear the **Use Encrypted Connection** check box.

6. Select **Next** to continue.

7. In **Navigator**, select the data you require, and then select **Transform data**.

   ![Power Query Online Navigator showing the Human Resources employee data.](./media/azure-sql-database/navigator-online.png)

## Connect using advanced options

Both Power Query Desktop and Power Query Online provide a set of advanced options that you can add to your query if needed.

![Display of advanced options available in Power Query.](./media/azure-sql-database/advanced-options.png)

The following table lists all of the advanced options you can set in Power Query Desktop and Power Query Online.

| Advanced option | Description |
| --------------- | ----------- |
| Command timeout in minutes | If your connection lasts longer than 10 minutes (the default timeout), you can enter another value in minutes to keep the connection open longer. This option is only available in Power Query Desktop. |
| SQL statement | For information, go to [Import data from a database using native database query](../native-database-query.md). |
| Include relationship columns | If checked, includes columns that might have relationships to other tables. If this box is cleared, you won’t see those columns. |
| Navigate using full hierarchy | If checked, the navigator displays the complete hierarchy of tables in the database you're connecting to. If cleared, the navigator displays only the tables whose columns and rows contain data. |
| Enable SQL Server Failover support | If checked, when a node in the Azure SQL [failover group](/azure/azure-sql/database/auto-failover-group-overview?tabs=azure-powershell) isn't available, Power Query moves from that node to another when failover occurs. If cleared, no failover occurs. |

Once you've selected the advanced options you require, select **OK** in Power Query Desktop or **Next** in Power Query Online to connect to your Azure SQL database.

## Troubleshooting

### Always Encrypted columns

Power Query doesn't support 'Always Encrypted' columns.
