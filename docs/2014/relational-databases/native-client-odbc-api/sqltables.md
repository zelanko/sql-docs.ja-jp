---
title: SQLTables |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b57c9e62115f7e30dccee569fa32a12545dddaac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177975"
---
# <a name="sqltables"></a>SQLTables
  SQLTables は静的サーバー カーソルで実行できます。 SQLTables を更新可能な (動的カーソルまたはキーセット カーソル) で実行するとは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 SQLTables からすべてのテーブルをレポートするデータベース、 *CatalogName*パラメーターは SQL_ALL_CATALOGS およびその他のすべてのパラメーターには、既定値 (NULL ポインター) が含まれています。  
  
 報告するために使用可能なカタログ、スキーマ、およびテーブル型は、SQLTables は、空の文字列 (長さが 0 バイトのポインター) 特別な用途をによりします。 空文字列は、既定値 (NULL ポインター) ではありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables では、いずれかに関する情報の名前と一致するテーブルを返します*TableName*は、現在のユーザーによって所有されているとします。  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE が、既定値の SQL_SS_NAME_SCOPE_TABLE ではなく sql_ss_name_scope_table_type である場合、SQLTables はテーブルの種類に関する情報を返します。 SQLTables によって返される結果セットの列 4 でテーブル型に対して返される TABLE_TYPE 値は、テーブル型です。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](sqlsetstmtattr.md)です。  
  
 テーブル、ビュー、およびシノニムは、テーブル型によって使用される名前空間とは異なる、共通の名前空間を共有します。 テーブルとビューを同じ名前にすることはできませんが、同じ名前のテーブルとテーブル型を同じカタログおよびスキーマ内に配置することはできます。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
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
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  