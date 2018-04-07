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
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 5f009cf311c1eb395915e017bf202abea5ae5290
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL、または OLE DB Driver for SQL Server は、SQL Server の OLE DB ドライバーを参照する同じ意味で使用される用語です。

## <a name="different-generations-of-ole-db-drivers"></a>OLE DB ドライバーのさまざまな世代

SQL Server の Microsoft OLE DB プロバイダーの 3 つの個別の世代があります。

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1.Microsoft OLE DB Provider for SQL Server (SQLOLEDB)
[Microsoft OLE DB Provider for SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) がまだの一部として出荷[Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx)です。 もはやに維持されませんし、このドライバーを使用して、新規の開発をお勧めできません。 


### <a name="2-sql-server-native-client-snac"></a>2.SQL Server Native Client (SNAC)
以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[は、SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md)に同梱されている OLE DB プロバイダーであり、OLE DB プロバイダー インターフェイス (SQLNCLI) が含まれています[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を通じて[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。

[2011年で非推奨と発表](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)し、このドライバーを使用して、新規の開発をお勧めできません。 SNAC ライフ サイクル、および利用可能なダウンロードの詳細についてを参照してください[説明 SNAC ライフ サイクル](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)です。

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3.Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)
OLE DB が[undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)と 2018年でリリースされ、ダウンロードが[ここ](https://go.microsoft.com/fwlink/?linkid=871294)です。

新しい OLE DB プロバイダーが呼び出されます Microsoft OLE DB ドライバーの SQL Server (MSOLEDBSQL)。 新しいプロバイダーは、今後、最新のサーバー機能と更新されます。

> [!NOTE]
> SQL Server の新しい Microsoft OLE DB Driver を使用して、既存のアプリケーションには、SQLOLEDB または SQLNCLI, から MSOLEDBSQL に、接続文字列を変換する計画してください。   

SQL Server の機能の OLE DB ドライバーに関する情報:

-   [LocalDB 用 OLE DB Driver for SQL Server のサポート](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [メタデータの検出](../oledb/features/metadata-discovery.md)  

-   [OLE DB Driver for SQL Server の UTF-16 のサポート](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [拡張イベント ログの診断情報へのアクセス](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>参照  
[SQL Server の OLE DB ドライバーをインストールします。](../oledb/applications/installing-oledb-driver-for-sql-server.md)     
[OLE DB Driver for SQL Server の機能](../oledb/features/oledb-driver-for-sql-server-features.md )     
