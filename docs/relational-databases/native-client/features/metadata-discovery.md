---
title: メタデータの検出 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d822362e9f9f7e70e4421056383aae8ddef03dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303363"
---
# <a name="metadata-discovery"></a>メタデータの検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  メタデータ検出の改善により[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クエリの実行から返される列またはパラメーターのメタデータが、クエリを実行する前に指定したメタデータ形式と同じか互換性があることを、ネイティブ クライアント アプリケーションで確認できます。 クエリの実行後に返されたメタデータにクエリの実行前に指定したメタデータ形式との互換性がない場合は、エラーが発生します。  
  
 bcp 関数と ODBC 関数、および IBCPSession インターフェイスと IBCPSession2 インターフェイスでは、遅延読み取り (遅延メタデータ検出) を指定して、クエリ出力操作でメタデータ検出を回避できます。 その結果、パフォーマンスが向上し、メタデータ検出のエラーを回避できます。  
  
 ネイティブ クライアントを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アプリケーションを開発[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]し、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]より前のバージョンのサーバーに接続する場合、メタデータ検出機能はサーバーのバージョンに対応します。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の bcp 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 bcp_setbulkmode[を使用](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)してメタデータ形式を指定する場合にも、パフォーマンスが向上します。  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)は、bcp_readfmtの動作を制御するための新しい*e オプション*を持っています: **BCPDELAYREADFMT**.  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の ODBC 関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では次の OLE DB メンバー関数が機能強化され、メタデータ検出機能が向上しています。  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (詳細は「[ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)」を参照)  
  
 IBCPSession::BCPSetBulkMode を使用してメタデータ形式を指定したときのパフォーマンスも向上しています。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でのメタデータ検出機能の強化は、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] への次の 2 つのストアド プロシージャの追加により実現されました。  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
