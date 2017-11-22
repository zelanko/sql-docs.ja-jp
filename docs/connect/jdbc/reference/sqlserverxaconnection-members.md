---
title: "SQLServerXAConnection のメンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88fc82e655317b6dadd5795c575d58d8edec3040
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverxaconnection-members"></a>SQLServerXAConnection のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(から継承された[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) 渡されたイベント リスナーを登録できるように、この接続オブジェクトでイベントが発生したときに通知されます。|  
|[閉じる](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(から継承された[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) 接続オブジェクトが表す物理的な接続を閉じます。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(から継承された[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) 接続オブジェクトが表す物理的な接続用のオブジェクト ハンドルを作成します。|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|取得、 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)これの参加を管理するトランザクション マネージャーが使用するオブジェクト[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)分散トランザクション内のオブジェクト。|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(から継承された[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) 特定のイベント リスナーを削除します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener、close、getConnection、removeConnectionEventListener|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|javax.sql.PooledConnection|addConnectionEventListener、close、getConnection、removeConnectionEventListener|  
  
## <a name="see-also"></a>参照  
 [SQLServerXAConnection クラス](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
