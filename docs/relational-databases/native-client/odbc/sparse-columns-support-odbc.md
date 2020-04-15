---
title: スパース列のサポート (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2dd987453202af2d7761e70193f8a0968f4ad38d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303708"
---
# <a name="sparse-columns-support-odbc"></a>スパース列のサポート (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC でのスパース列のサポートについて説明します。 スパース列の ODBC サポートの例については、「 ス[パース列を持つテーブルの SQLColumns の呼び出し](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)」を参照してください。 スパース列の詳細については、「 [SQL Server ネイティブ クライアントでのスパース列のサポート](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md)」を参照してください。  
  
## <a name="statement-metadata"></a>ステートメント メタデータ  
 アプリケーション パラメーター記述子 (APD) の記述子フィールドと SQL_SOPT_SS_NAME_SCOPE ステートメント属性は、追加の値 SQL_SS_NAME_SCOPE_EXTENDED および SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET を受け入れます。 これらの値は、 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)によって返される結果セットに含める列を指定します。 SQL_SOPT_SS_NAME_SCOPEの詳細については、「 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)」を参照してください。  
  
 新しい実装行記述子 (IRD) は、SQL_CA_SS_IS_COLUMN_SETと呼ばれる読み取り専用 SQLSMALLINT フィールドを使用して、列が XML **column_set**値かどうかを判別できます。 SQL_CA_SS_IS_COLUMN_SET は、値 SQL_TRUE および SQL_FALSE を受け取ります。  
  
## <a name="catalog-metadata"></a>カタログ メタデータ  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)の結果セットに、2 つの列 (SS_IS_SPARSEとSS_IS_COLUMN_SET) が追加されました。  
  
## <a name="odbc-function-support-for-sparse-columns"></a>ODBC 関数によるスパース列のサポート  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でスパース列をサポートするために、次の ODBC 関数が更新されました。  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
