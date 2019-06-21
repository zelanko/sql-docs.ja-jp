---
title: setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: eddf7b58456a4730ff783ab4f53a9911da06d8db
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782964"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 特定の接続のインスタンスの動作を指定します。 この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 ときに、設定は、< = 1 解除-準備で準備されたステートメントを閉じる操作が直ちに実行されます。 値が > 1 に設定されている場合の頻度が高すぎる sp_unprepare の呼び出しのオーバーヘッドを回避するためにこれらの呼び出しはまとめてバッチします。


## <a name="syntax"></a>構文  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>パラメーター  
 *thresholdValue*  
 
 新しい値、 **serverPreparedStatementDiscardThreshold**接続プロパティです。  
 
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
