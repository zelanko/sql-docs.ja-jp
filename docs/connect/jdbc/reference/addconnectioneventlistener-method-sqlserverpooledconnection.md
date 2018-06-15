---
title: addConnectionEventListener メソッド (SQLServerPooledConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: 6482521780045b1d5f0482731c1b6f8e2f5f3571
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828267"
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
  
  
