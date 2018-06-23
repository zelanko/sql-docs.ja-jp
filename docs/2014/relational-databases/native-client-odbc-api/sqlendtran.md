---
title: SQLEndTran | Microsoft Docs
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
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 360c015dba746f110327804a457bb6e5c1e83212
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175334"
---
# <a name="sqlendtran"></a>SQLEndTran
  既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはステートメントの関連付けられたカーソルを閉じるときに**SQLEndTran**がコミットまたはロールバック操作します。 サーバー カーソルは、静的カーソルでない限り、閉じられます。 ときに**SQLEndTran**がコミットまたはロールバック操作、ステートメントの関連付けられたカーソルの動作はによって設定ドライバー固有のODBC接続属性SQL_COPT_SS_PRESERVE_CURSORSの値によって決まります[SQLSetConnectAttr](sqlsetconnectattr.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)   
 [SQLEndTran 関数](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  