---
title: "setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 427258eb9d216f867e244ebb1b80af9036a09a66
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 特定の接続のインスタンスの動作を指定します。 この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 ときに、設定 < = 1 解除-準備操作は、準備されたステートメント閉じるで直ちに実行されます。 > 1 の値が設定されている場合が頻繁すぎる sp_unprepare の呼び出しのオーバーヘッドを避けるためにこれらの呼び出しがまとめて処理します。


## <a name="syntax"></a>構文  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>パラメーター  
 *thresholdValue*  
 
 新しい値、 **serverPreparedStatementDiscardThreshold**接続プロパティです。  
 
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
