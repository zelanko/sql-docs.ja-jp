---
title: SQLFreeStmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa7e597bcfa80d7d45064c844986018d64617d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63190309"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
  **SQLFreeStmt**は、ODBC 3.0 以降では推奨されません。 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC ドライバーでは、 **SQLFreeStmt**に対して定義されているすべての*オプション*値がサポートされています。 ただし、 [Sqlcloセキュリティー](sqlclosecursor.md)、 [SQLBindParameter](sqlbindparameter.md)、 [SQLBindCol](sqlbindcol.md)、 **SQLSetDescField**、および[sqlfreehandle](sqlfreehandle.md)は、 **SQLFreeStmt**の関数を置き換えたり複製したりする必要があり、代わりに使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLFreeStmt 関数](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
