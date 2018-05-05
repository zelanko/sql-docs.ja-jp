---
title: SQLTables |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6d2d6641ca7fb9aa296817186082d3a6b3b6a0bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLTables は静的サーバー カーソルで実行できます。 SQLTables を更新可能な (動的カーソルまたはキーセット カーソル) で実行するとは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 SQLTables からすべてのテーブルをレポートするデータベース、 *CatalogName*パラメーターは SQL_ALL_CATALOGS およびその他のすべてのパラメーターには、既定値 (NULL ポインター) が含まれています。  
  
 報告するために使用可能なカタログ、スキーマ、およびテーブル型は、SQLTables は、空の文字列 (長さが 0 バイトのポインター) 特別な用途をによりします。 空文字列は、既定値 (NULL ポインター) ではありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables では、いずれかに関する情報の名前と一致するテーブルを返します*TableName*は、現在のユーザーによって所有されているとします。  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE が、既定値の SQL_SS_NAME_SCOPE_TABLE ではなく sql_ss_name_scope_table_type である場合、SQLTables はテーブルの種類に関する情報を返します。 SQLTables によって返される結果セットの列 4 でテーブル型に対して返される TABLE_TYPE 値は、テーブル型です。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 テーブル、ビュー、およびシノニムは、テーブル型によって使用される名前空間とは異なる、共通の名前空間を共有します。 テーブルとビューを同じ名前にすることはできませんが、同じ名前のテーブルとテーブル型を同じカタログおよびスキーマ内に配置することはできます。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="example"></a>例  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>参照  
 [SQLTables 関数](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
