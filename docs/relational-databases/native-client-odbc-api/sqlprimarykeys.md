---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 27eef998bf148e9503a415d8d38bceaecd497f38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68131247"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  または、一意の行識別子として使用できる複数の列をテーブルとして使用することがあり、PRIMARY KEY 制約なしで作成されたテーブルが空の結果セットに SQLPrimaryKeys を返します。 ODBC 関数[SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md)レポート行の主キーのないテーブルの識別子の候補とします。  
  
 SQLPrimaryKeys は値が存在するかどうかに関係なく SQL_SUCCESS を返します*CatalogName*、 *SchemaName*、または*TableName*パラメーター。 これらのパラメーターに無効な値を使用する場合は、SQL_NO_DATA が返さ SQLFetch します。  
  
 SQLPrimaryKeys は静的サーバー カーソルで実行できます。 SQLPrimaryKeys を更新可能な (動的またはキーセット) カーソルで実行するとは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバー上のテーブルに関する情報のレポートをサポートの 2 つの部分名をそのまま使用して、 *CatalogName*パラメーター。*Linked_Server_Name.Catalog_Name*します。  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE が、既定値の SQL_SS_NAME_SCOPE_TABLE ではなく sql_ss_name_scope_table_type である場合、値、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)します。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLPrimaryKeys 関数](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
