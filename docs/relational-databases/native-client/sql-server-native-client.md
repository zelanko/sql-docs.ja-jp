---
title: SQL Server Native Client |Microsoft Docs
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e11bc1094f7bab993eb67542c16360e874db87f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031778"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC、または SQL Server Native Client では、SQL Server 用 ODBC および OLE DB ドライバーを参照する同じ意味で使用されている用語です。

> [!IMPORTANT] 
> SQL Server Native Client (SQLNCLI) は非推奨と新しい開発作業で使用する勧めしません。 代わりに、新しい使用[Microsoft OLE DB Driver for SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) server の最新の機能と更新されます。

> [!NOTE]
> 詳細については、および SNAC または ODBC ドライバーをダウンロードするには、「、 [SNAC ライフ サイクル ブログ投稿の説明](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)します。
> SQL Server 用 ODBC ドライバーの詳細については、次を参照してください。 [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)します。  

 については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共に Native Client の機能がリリースされた[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、SQL Server native Client の最後の使用可能なバージョン。

-   [SQL Server Native Client における LocalDB のサポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [SQL Server Native Client 11.0 での UTF-16 のサポート](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [SQL Server Native Client の HADR サポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [拡張イベント ログの診断情報へのアクセス](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は、Windows 7 SDK の標準の ODBC に追加された 3 つの機能をサポートしています。  

-   接続関連の操作での非同期実行。 詳細については、次を参照してください。[非同期実行](https://go.microsoft.com/fwlink/?LinkID=191493)します。  

-   C データ型の機能拡張。 詳細については、次を参照してください。 [ODBC における C データ型](https://go.microsoft.com/fwlink/?LinkID=191495)します。  

     この機能をサポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client、SQLGetDescField を返せる**SQL_C_SS_TIME2** (の**時間**型) または**SQL_C_SS_TIMESTAMPOFFSET** (**datetimeoffset**) の代わりに**SQL_C_BINARY**場合、アプリケーションで ODBC 3.8 が使用されます。 詳細については、次を参照してください。 [ODBC の日付と時刻の強化に対するデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)します。  

-   呼び出す**SQLGetData**小さなバッファーを複数回に大きなパラメーター値を取得します。 詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](https://go.microsoft.com/fwlink/?LinkID=191494)します。  

 次のトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client の動作の変更点について説明します。  

-   呼び出すときに**icommandwithparameters::setparameterinfo**に渡される値、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、次を参照してください。 [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)します。  

-   **SQLDescribeParam** ODBC 仕様準拠した値は一貫して返します。 詳細については、次を参照してください。 [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md)します。  

-   [文字変換処理での ODBC ドライバーの動作の変更](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>関連項目  
[SQL Server Native Client をインストールします。](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [SQL Server Native Client の機能](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
