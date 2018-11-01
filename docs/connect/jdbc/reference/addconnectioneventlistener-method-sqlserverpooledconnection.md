---
title: addConnectionEventListener メソッド (SQLServerPooledConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fbd278bfa95d0697d7435ccac132a60112b32d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799610"
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>addConnectionEventListener メソッド (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) オブジェクトでイベントが発生した場合に通知を受けるように、渡されたイベント リスナーを登録します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *リスナー*  
  
 ConnectionEventListener オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 この addConnectionEventListener メソッドは、javax.sql.PooledConnection インターフェイスで addConnectionEventListener メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerPooledConnection メソッド](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection のメンバー](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection クラス](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
