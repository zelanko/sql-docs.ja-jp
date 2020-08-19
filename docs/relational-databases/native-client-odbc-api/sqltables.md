---
description: SQLTables
title: SQLTables |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 735a0fa33e894f6642b6183a517da0d61123a6a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420746"
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  SQLTables は、静的サーバーカーソルで実行できます。 更新可能なカーソル (動的カーソルまたはキーセットカーソル) で SQLTables を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。  
  
 *CatalogName*パラメーターが SQL_ALL_CATALOGS、他のすべてのパラメーターに既定値 (NULL ポインター) が含まれている場合、sqltables はすべてのデータベースのテーブルを報告します。  
  
 使用可能なカタログ、スキーマ、およびテーブルの種類をレポートするために、SQLTables は空の文字列 (長さゼロのバイトポインター) を特別に使用します。 空文字列は、既定値 (NULL ポインター) ではありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。  
  
 SQLTables は、名前が *TableName* に一致し、現在のユーザーが所有しているテーブルに関する情報を返します。  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE の値が既定値の SQL_SS_NAME_SCOPE_TABLE ではなく SQL_SS_NAME_SCOPE_TABLE_TYPE の場合、SQLTables はテーブル型に関する情報を返します。 SQLTables によって返される結果セットの列4のテーブル型に対して返される TABLE_TYPE 値はテーブル型です。 SQL_SOPT_SS_NAME_SCOPE の詳細については、「 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)」を参照してください。  
  
 テーブル、ビュー、およびシノニムは、テーブル型によって使用される名前空間とは異なる、共通の名前空間を共有します。 テーブルとビューを同じ名前にすることはできませんが、同じ名前のテーブルとテーブル型を同じカタログおよびスキーマ内に配置することはできます。  
  
 テーブル値パラメーターの詳細については、「 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
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
 [SQLTables 関数](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
