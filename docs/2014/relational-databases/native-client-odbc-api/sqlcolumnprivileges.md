---
title: SQLColumnPrivileges |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6462213fddd646c1461f0975dc89b151c192de3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425731"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges**値が存在するかどうかに関係なく SQL_SUCCESS を返します、*CatalogName*、 *SchemaName*、 *TableName*、または*ColumnName*パラメーター。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLColumnPrivileges**静的サーバー カーソルで実行できます。 実行しようとすると、 **SQLColumnPrivileges**更新可能な (動的またはキーセット) カーソルでは、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバー上のテーブルに関する情報のレポートをサポートの 2 つの部分名をそのまま使用して、 *CatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>参照  
 [SQLColumnPrivileges 関数](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
