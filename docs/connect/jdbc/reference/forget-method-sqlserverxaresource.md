---
title: forget メソッド (SQLServerXAResource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerXAResource.forget
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d83138d-aa45-4d94-9da6-fdfe7ed28edc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abca1fec57ca8b4e181515683a16613c574bff85
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="forget-method-sqlserverxaresource"></a>forget メソッド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  リソース マネージャーに対し、ヒューリスティックに決着されたトランザクション ブランチを無視するよう指示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void forget(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *xid*  
  
 Xid オブジェクト。  
  
## <a name="exceptions"></a>例外  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>解説  
 この破棄メソッドは、破棄、javax.transaction.xa.XAResource インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメソッド](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
