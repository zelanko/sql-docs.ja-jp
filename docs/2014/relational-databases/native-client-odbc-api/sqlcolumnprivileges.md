---
title: SQLColumnPrivileges |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: rothja
ms.author: jroth
ms.openlocfilehash: bf46fed47817ed94ea2382f2147df254f2986aec
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022752"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **Sqlcolumnprivileges**は、*CatalogName*、 *SchemaName*、 *TableName*、または*ColumnName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。 これらのパラメーターで無効な値が使用されている場合、 **Sqlfetch**は SQL_NO_DATA を返します。  
  
 **Sqlcolumnprivileges**は、静的サーバーカーソルで実行できます。 更新可能なカーソル (動的カーソルまたはキーセットカーソル) に対して**Sqlcolumnprivileges**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。  
  
## <a name="see-also"></a>参照  
 [SQLColumnPrivileges 関数](https://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
