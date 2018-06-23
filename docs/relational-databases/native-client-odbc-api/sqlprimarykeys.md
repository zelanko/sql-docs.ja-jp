---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 85426a83b8134c468c64d043861e974658242f31
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702483"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  または、一意の行識別子として使用できる複数の列をテーブルとして使用することがあり、テーブルの主キー制約なしで作成が空の結果を SQLPrimaryKeys セットを返します。 ODBC 関数[SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md)行の主キーのないテーブルの id の候補をレポートします。  
  
 SQLPrimaryKeys は、値が存在するかどうかに関係なく SQL_SUCCESS を返します*CatalogName*、 *SchemaName*、または*TableName*パラメーター。 SQLFetch 無効な値は、これらのパラメーターで使用すると SQL_NO_DATA が返されます。  
  
 SQLPrimaryKeys は静的サーバー カーソルで実行できます。 SQLPrimaryKeys を更新可能な (動的カーソルまたはキーセット カーソル) で実行するとは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE 値が、既定値の SQL_SS_NAME_SCOPE_TABLE ではなく sql_ss_name_scope_table_type である、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLPrimaryKeys 関数](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
