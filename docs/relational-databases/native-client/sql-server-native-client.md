---
title: SQL Server Native Client |Microsoft Docs
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a1f60dff72b14e29572a4d255ad8473d6ed1672d
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43081954"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC、または SQL Server Native Client では、SQL Server 用 ODBC および OLE DB ドライバーを参照する同じ意味で使用されている用語です。

**注:** このドライバーを使用して、新規の開発をお勧めできません。 新しい OLE DB プロバイダーが呼び出される、 [Microsoft OLE DB Driver for SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) 今後、最新のサーバー機能と更新されます。


**詳細については、および SNAC または ODBC ドライバーをダウンロードするを参照してください。 [SNAC ライフ サイクルを説明した](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)します。**

SQL Server 用 ODBC ドライバーの詳細については、次を参照してください。 [Microsoft ODBC Driver for SQL Server on Windows](https://msdn.microsoft.com/library/jj730314(v=sql.110).aspx)します。  またを参照してください[SQL Server の新しい Microsoft ODBC Drivers の概要](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)、および[ODBC Driver 13.1 for SQL Server がリリースされた](https://blogs.technet.microsoft.com/dataplatforminsider/2016/08/03/odbc-driver-13-1-for-sql-server-released/)します。  

 については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共に Native Client の機能がリリースされた[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、SQL Server native Client の最後の使用可能なバージョン。

-   [SQL Server Native Client における LocalDB のサポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [SQL Server Native Client 11.0 での UTF-16 のサポート](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [SQL Server Native Client の HADR サポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [拡張イベント ログの診断情報へのアクセス](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は、Windows 7 SDK の標準の ODBC に追加された 3 つの機能をサポートしています。  

-   接続関連の操作での非同期実行。 詳細については、次を参照してください。[非同期実行](http://go.microsoft.com/fwlink/?LinkID=191493)します。  

-   C データ型の機能拡張。 詳細については、次を参照してください。 [ODBC における C データ型](http://go.microsoft.com/fwlink/?LinkID=191495)します。  

     この機能をサポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client、SQLGetDescField を返せる**SQL_C_SS_TIME2** (の**時間**型) または**SQL_C_SS_TIMESTAMPOFFSET** (**datetimeoffset**) の代わりに**SQL_C_BINARY**場合、アプリケーションで ODBC 3.8 が使用されます。 詳細については、次を参照してください。 [ODBC の日付と時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)します。  

-   呼び出す**SQLGetData**小さなバッファーを複数回に大きなパラメーター値を取得します。 詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](http://go.microsoft.com/fwlink/?LinkID=191494)します。  

 次のトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client の動作の変更点について説明します。  

-   呼び出すときに**icommandwithparameters::setparameterinfo**に渡される値、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、次を参照してください。 [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)します。  

-   **SQLDescribeParam** ODBC 仕様準拠した値は一貫して返します。 詳細については、次を参照してください。 [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md)します。  

-   [文字変換処理での ODBC ドライバーの動作の変更](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>関連項目  
[SQL Server Native Client をインストールします。](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [SQL Server Native Client の機能](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
