---
title: スパース列のサポート (ODBC) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 81e4dad9a5f60c4fa1a6dd7427487a3785da6221
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950127"
---
# <a name="sparse-columns-support-odbc"></a>スパース列のサポート (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC でのスパース列のサポートについて説明します。 スパース列に対する ODBC サポートを示すサンプルについては、次を参照してください。[スパース列とテーブルに対する SQLColumns を呼び出す](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)です。 スパース列の詳細については、次を参照してください。 [SQL Server Native Client におけるスパース列のサポート](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md)です。  
  
## <a name="statement-metadata"></a>ステートメント メタデータ  
 アプリケーション パラメーター記述子 (APD) の記述子フィールドと SQL_SOPT_SS_NAME_SCOPE ステートメント属性は、追加の値 SQL_SS_NAME_SCOPE_EXTENDED および SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET を受け入れます。 これらの値がによって返される結果セットに含まれる列を指定[SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)です。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 列が XML かどうかを判断する、新しい実装行記述子 (IRD) の SQL_CA_SS_IS_COLUMN_SET という読み取り専用 SQLSMALLINT フィールドを使用できます**column_set**値。 SQL_CA_SS_IS_COLUMN_SET は、値 SQL_TRUE および SQL_FALSE を受け取ります。  
  
## <a name="catalog-metadata"></a>カタログ メタデータ  
 2 つ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の結果セットに特定の列 (SS_IS_SPARSE と SS_IS_COLUMN_SET) が追加された[SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)です。  
  
## <a name="odbc-function-support-for-sparse-columns"></a>ODBC 関数によるスパース列のサポート  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client でスパース列をサポートするために、次の ODBC 関数が更新されました。  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [Sqlsetdescfield による](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client (&) #40";"ODBC"&"#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
