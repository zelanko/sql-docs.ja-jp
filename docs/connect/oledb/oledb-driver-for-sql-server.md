---
title: OLE DB Driver for SQL Server |Microsoft ドキュメント
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
description: ''
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 89e66fe2c61ae17a43e2a58071ba04374f33ea04
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL、または OLE DB Driver for SQL Server は、SQL Server の OLE DB ドライバーを参照する同じ意味で使用されている用語です。

## <a name="different-incarnations-of-ole-db-drivers"></a>OLE DB ドライバーのさまざまなエディション

SQL Server の Microsoft OLE DB プロバイダーの次の 3 つの異なる段階があります。


### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1.Microsoft OLE DB Provider for SQL Server (SQLOLEDB)

[Microsoft OLE DB Provider for SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) がまだの一部として出荷[Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx)です。 このドライバーを使用して、新規の開発には推奨されません。


### <a name="2-sql-server-native-client-snac"></a>2.SQL Server Native Client (SNAC)

SQL Server 2005 以降で、[は、SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) SQL Server 2005 で SQL Server 2017 に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれています。

[2011年で非推奨と発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)し、このドライバーを使用して、新規の開発をお勧めできません。


### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3.Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)

OLE DB が[2017年で undeprecated として発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)です。 2018 の計画済みの新しいリリースが発表されました。

新しい OLE DB プロバイダーが呼び出されます Microsoft OLE DB ドライバーの SQL Server (MSOLEDBSQL)。 新しいプロバイダーは、今後、最新のサーバー機能と更新されます。

SQL Server の機能の OLE DB ドライバーに関する情報:

-   [SQL Server Support for LocalDB 用の OLE DB ドライバー](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [メタデータの検出](../oledb/features/metadata-discovery.md)  

-   [SQL Server の OLE DB ドライバーの utf-16 のサポート](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [SQL Server Support for High Availability, Disaster Recovery の OLE DB ドライバー](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [拡張イベント ログの診断情報へのアクセス](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>参照  
[SQL Server の OLE DB ドライバーをインストールします。](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
 [SQL Server 機能の OLE DB ドライバー](../oledb/features/oledb-driver-for-sql-server-features.md )  
