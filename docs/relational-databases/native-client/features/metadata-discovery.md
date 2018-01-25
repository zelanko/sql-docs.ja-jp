---
title: "メタデータの検出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d847a3f0a6a577b82de4bf060cdb3fdb44a71f5a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="metadata-discovery"></a>メタデータの検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  メタデータ検出機能が強化[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]により[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]書式を設定する前に指定したネイティブ クライアント アプリケーションが、クエリの実行から返された列またはパラメーター メタデータが同一でも、メタデータと互換性のあることを確認するにはクエリを実行しました。 クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。  
  
 bcp 関数と ODBC 関数、および IBCPSession インターフェイスと IBCPSession2 インターフェイスでは、遅延読み取り (遅延メタデータ検出) を指定して、クエリ出力操作でメタデータ検出を回避できます。 その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。  
  
 使用して、アプリケーションを開発する場合は[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client に[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]サーバー バージョンへの接続がよりも前[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、メタデータ検出機能は、サーバーのバージョンに対応します。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の bcp 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 使用してメタデータ形式を指定する場合にも、パフォーマンスを改善表示されます[bcp_setbulkmode](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)です。  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)が新しい*eOption* bcp_readfmt の動作を制御する: **BCPDELAYREADFMT**です。  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の ODBC 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters::getparameterinfo (を参照してください[ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)詳細)  
  
 IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定する場合にも、パフォーマンスを改善を表示されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でのメタデータ検出機能の強化は、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] への次の 2 つのストアド プロシージャの追加により実現されました。  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
