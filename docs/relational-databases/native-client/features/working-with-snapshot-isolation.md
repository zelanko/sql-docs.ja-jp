---
title: スナップショット分離を使用した作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06e4964dcab38087119343ab2fbc900f29d60d14
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303153"
---
# <a name="working-with-snapshot-isolation"></a>スナップショット分離を使用した作業
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、OLTP (オンライン トランザクション処理) アプリケーションのコンカレンシーの強化を目的として、新しく "スナップショット" 分離レベルが導入されました。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、コンカレンシーはロックだけを基にしていました。そのため、アプリケーションによってはブロックやデッドロックなどの問題が生じることがありました。 スナップショット分離は行のバージョン管理の機能強化に依存しており、リーダーとライターのブロッキングを回避することでパフォーマンスを向上することを目的としています。  
  
 スナップショット分離の下で開始されたトランザクションは、トランザクションの開始時点のデータベース スナップショットを読み取ります。 この結果、スナップショット トランザクション コンテキスト内でキーセット サーバー カーソル、動的サーバー カーソル、および静的サーバー カーソルを開くと、これらのカーソルはシリアル化可能なトランザクション内で開かれた静的カーソルとほぼ同様に動作します。 また、スナップショット分離レベルの下でカーソルが開かれると、ロックが設定されず、サーバーでのブロッキングを減少させることができます。  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダには、 で導入されたスナップショット分離を[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]利用する機能強化が追加されています。 具体的には、DBPROPSET_DATASOURCEINFO プロパティ セットと DBPROPSET_SESSION プロパティ セットへ変更が加えられています。  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 DBPROP_SUPPORTEDTXNISOLEVELS プロパティで使用される DBPROPVAL_TI_SNAPSHOT 値が追加され、DBPROPSET_DATASOURCEINFO プロパティ セットではスナップショット分離レベルがサポートされるようになりました。 この新しい値は、データベースでバージョン管理が有効になっているかどうかにかかわらず、スナップショット分離レベルがサポートされることを示します。 次に、DBPROP_SUPPORTEDTXNISOLEVELS の値の一覧を示します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|型 : VT_I4<br /><br /> R/W: 読み取り専用<br /><br /> 説明 : サポートされるトランザクション分離レベルを指定するビットマスク。 次の値を 0 個以上指定できます。<br /><br /> DBPROPVAL_TI_CHAOS <br /><br /> DBPROPVAL_TI_READUNCOMMITTED <br /><br /> DBPROPVAL_TI_BROWSE <br /><br /> DBPROPVAL_TI_CURSORSTABILITY <br /><br /> DBPROPVAL_TI_READCOMMITTED <br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>DBPROPSET_SESSION  
 DBPROP_SESS_AUTOCOMMITISOLEVELS プロパティで使用される DBPROPVAL_TI_SNAPSHOT 値が追加され、DBPROPSET_SESSION プロパティ セットではスナップショット分離レベルがサポートされるようになりました。 この新しい値は、データベースでバージョン管理が有効になっているかどうかにかかわらず、スナップショット分離レベルがサポートされることを示します。 次に、DBPROP_SESS_AUTOCOMMITISOLEVELS の値の一覧を示します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|型 : VT_I4<br /><br /> R/W: 読み取り専用<br /><br /> 説明 : 自動コミット モードのときのトランザクション分離レベルを示すビットマスクを指定します。 このビットマスクには、DBPROP_SUPPORTEDTXNISOLEVELS に設定できる値と同じ値を設定できます。|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] を使用しているときに DBPROPVAL_TI_SNAPSHOT を設定すると、エラー DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED が発生します。  
  
 トランザクションでスナップショット分離がサポートされる方法については、「[ローカル トランザクションのサポート](../../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)」を参照してください。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 ネイティブ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、スナップショット分離のサポートを提供しますが[、SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)関数と[SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)関数に対する機能強化が行われました。  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 **SQLSetConnectAttr**関数は、SQL_COPT_SS_TXN_ISOLATION属性の使用をサポートするようになりました。 SQL_COPT_SS_TXN_ISOLATION を SQL_TXN_SS_SNAPSHOT に設定すると、トランザクションがスナップショット分離レベルで実行されることが報告されます。  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)関数は、SQL_TXN_ISOLATION_OPTION情報の種類に追加されたSQL_TXN_SS_SNAPSHOT値をサポートするようになりました。  
  
 トランザクションでのスナップショット分離のサポート方法については、「[カーソル トランザクション分離レベル](../../../relational-databases/native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ネイティブ クライアントの機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [行セットのプロパティと動作](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
