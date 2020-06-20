---
title: メタデータの検出 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
ms.openlocfilehash: 0397d7f5588be7543f71819c93827819bd8d073f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047936"
---
# <a name="metadata-discovery"></a>メタデータの検出
  のメタデータ検出の [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 機能強化により、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ネイティブクライアントアプリケーションでは、クエリの実行によって返される列またはパラメーターのメタデータが、クエリを実行する前に指定したメタデータ形式と同じか、または互換性があるかを確認できます。 クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。  
  
 bcp 関数と ODBC 関数、および IBCPSession インターフェイスと IBCPSession2 インターフェイスでは、遅延読み取り (遅延メタデータ検出) を指定して、クエリ出力操作でメタデータ検出を回避できます。 その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。  
  
 で Native Client を使用しているアプリケーションを開発している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] が、より前のサーバーバージョンに接続している場合 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 、メタデータ検出機能はサーバーのバージョンに対応します。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の bcp 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 [Bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)を使用してメタデータ形式を指定すると、パフォーマンスが向上します。  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)には、bcp_readfmt の動作を制御する新しい*eOption*があり `BCPDELAYREADFMT` ます。  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の ODBC 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (詳細は「[ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md)」を参照)  
  
 IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定したときのパフォーマンスも向上しています。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でのメタデータ検出機能の強化は、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] への次の 2 つのストアド プロシージャの追加により実現されました。  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
