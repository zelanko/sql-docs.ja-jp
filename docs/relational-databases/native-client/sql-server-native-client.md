---
title: 概要
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d175942c9d636221868ca12743e6dac79bb2ddcb
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388714"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SNAC 、または SQL Server ネイティブ クライアントは、SQL Server の ODBC および OLE DB ドライバーを参照するために同じ意味で使用されている用語です。

> [!IMPORTANT] 
> SQL Server ネイティブ クライアント (SQLNCLI) は非推奨のままであり、新しい開発作業に使用することはお勧めしません。 代わりに、新しい [Microsoft OLE DB Driver for SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) を使用します。これは、最新のサーバー機能で更新されます。

> [!NOTE]
> 詳細および SNAC ドライバまたは ODBC ドライバのダウンロードについては[、SNAC のライフサイクルの説明を参照してください](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)。
> SQL Server 用 ODBC ドライバーの詳細については、「 [SQL Server 用 ODBC ドライバー](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)」を参照してください。  

 で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]リリースされた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント機能に関する情報は、SQL Server ネイティブ クライアントの最新の利用可能なバージョンです。

-   [SQL Server Native Client における LocalDB のサポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [メタデータの検出](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [SQL Server Native Client 11.0 での UTF-16 のサポート](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [SQL Server Native Client の HADR サポート](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [拡張イベント ログの診断情報へのアクセス](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントの ODBC では、Windows 7 SDK で標準 ODBC に追加された 3 つの機能がサポートされています。  

-   接続関連の操作での非同期実行。 詳細については、「[非同期実行](https://go.microsoft.com/fwlink/?LinkID=191493)」を参照してください。  

-   C データ型の機能拡張。 詳細については[、「ODBC での C データ型](https://go.microsoft.com/fwlink/?LinkID=191495)」を参照してください。  

     ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントでこの機能をサポートするために、SQLGetDescField は、アプリケーションが ODBC 3.8 を使用する場合 **、SQL_C_BINARY**ではなく**SQL_C_SS_TIME2** (**時刻**型の場合) または**SQL_C_SS_TIMESTAMPOFFSET** (**日付オフセット**) を返します。 詳細については、「 [ODBC 日付と時刻の向上のためのデータ型のサポート](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)」を参照してください。  

-   大きなパラメーター値を取得するために、小さいバッファーを使用して**SQLGetData**を複数回呼び出します。 詳細については、「 [SQLGetData を使用した出力パラメータの取得](https://go.microsoft.com/fwlink/?LinkID=191494)」を参照してください。  

 次のトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client の動作の変更点について説明します。  

-   を呼び出すとき**は***、pwszName*パラメーターに渡される値が有効な識別子である必要があります。 詳細については、「[パラメーターを使用する」](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)を参照してください。  

-   **SQLDescribe パラム**は、ODBC 仕様準拠の値を常に返します。 詳細については、「 [SQL Describe パラム](../../relational-databases/native-client-odbc-api/sqldescribeparam.md)」を参照してください。  

-   [文字変換処理での ODBC ドライバーの動作の変更](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>関連項目  
[SQL Server ネイティブ クライアントのインストール](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [SQL Server Native Client の機能](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
