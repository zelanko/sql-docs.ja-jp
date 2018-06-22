---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb0dc440025730c278206a751a5ce741b69b0f6e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073248"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  または、一意の行識別子として使用できる複数の列をテーブルとして使用することがあり、テーブルの主キー制約なしで作成が空の結果を SQLPrimaryKeys セットを返します。 ODBC 関数[SQLSpecialColumns](sqlspecialcolumns.md)行の主キーのないテーブルの id の候補をレポートします。  
  
 SQLPrimaryKeys は、値が存在するかどうかに関係なく SQL_SUCCESS を返します*CatalogName*、 *SchemaName*、または*TableName*パラメーター。 SQLFetch 無効な値は、これらのパラメーターで使用すると SQL_NO_DATA が返されます。  
  
 SQLPrimaryKeys は静的サーバー カーソルで実行できます。 SQLPrimaryKeys を更新可能な (動的カーソルまたはキーセット カーソル) で実行するとは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE 値が、既定値の SQL_SS_NAME_SCOPE_TABLE ではなく sql_ss_name_scope_table_type である、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。 SQL_SOPT_SS_NAME_SCOPE の詳細については、次を参照してください。 [SQLSetStmtAttr](sqlsetstmtattr.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLPrimaryKeys 関数](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  