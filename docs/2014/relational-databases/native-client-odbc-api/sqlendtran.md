---
title: SQLEndTran |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: rothja
ms.author: jroth
ms.openlocfilehash: e5d44756131b6133baec69e34da11055a965e2da
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022734"
---
# <a name="sqlendtran"></a>SQLEndTran
  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、 **SQLEndTran**が操作をコミットまたはロールバックするときに、ステートメントに関連付けられたカーソルを閉じます。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 **SQLEndTran**が操作をコミットまたはロールバックする場合、ステートメントに関連付けられているカーソルの動作は、 [SQLSetConnectAttr](sqlsetconnectattr.md)によって設定される、ドライバー固有の ODBC 接続属性の値によって決定され SQL_COPT_SS_PRESERVE_CURSORS ます。  
  
## <a name="see-also"></a>参照  
 [ODBC API の実装の詳細](odbc-api-implementation-details.md)   
 [SQLEndTran 関数](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
