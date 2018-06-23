---
title: SQLColumnPrivileges |Microsoft ドキュメント
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
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c13c432b43be893cdc0612fe9ed54fc7b612b213
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076875"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges**値が存在するかどうかに関係なく SQL_SUCCESS を返します、*CatalogName*、 *SchemaName*、 *TableName*、または*ColumnName*パラメーター。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLColumnPrivileges**は静的サーバー カーソルで実行できます。 実行すると**SQLColumnPrivileges**更新可能な (動的カーソルまたはキーセット カーソル) では、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>参照  
 [SQLColumnPrivileges 関数](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  