---
title: addConnectionEventListener メソッド (SQLServerPooledConnection) |Microsoft ドキュメント
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
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eebf0878a8a98fc19f10152944138be875327ca1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>addConnectionEventListener メソッド (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これで、イベントが発生したときに通知されるように渡されたイベント リスナーを登録[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *リスナー*  
  
 ConnectionEventListener オブジェクトです。  
  
## <a name="remarks"></a>解説  
 この addConnectionEventListener メソッドは、javax.sql.PooledConnection インターフェイスの addConnectionEventListener メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerPooledConnection メソッド](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection のメンバー](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection クラス](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
