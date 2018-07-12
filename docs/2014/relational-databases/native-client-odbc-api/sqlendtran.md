---
title: SQLEndTran | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99f4c5a37cc16cfce70545e6f74822da97ad0637
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408107"
---
# <a name="sqlendtran"></a>SQLEndTran
  既定で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーがステートメントの関連付けられているカーソルを閉じるときに**SQLEndTran**コミットまたはロールバック操作を行います。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 ときに**SQLEndTran**がコミットまたはロールバック操作をステートメントの関連付けられているカーソルの動作はによって設定ドライバー固有のODBC接続属性SQL_COPT_SS_PRESERVE_CURSORSの値によって決まります[SQLSetConnectAttr](sqlsetconnectattr.md)します。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)   
 [SQLEndTran 関数](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
