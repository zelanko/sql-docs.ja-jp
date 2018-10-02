---
title: getServerPreparedStatementDiscardThreshold メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09762036b607f5d124ae50a333c99eff67649079
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633810"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  値を返します**serverPreparedStatementDiscardThreshold**接続プロパティです。 この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 ときに、設定は、< = 1 unprepare アクション準備されたステートメントを閉じるには直ちに実行されます。 この値が > 1 に設定する場合これらの呼び出しは sp_unprepare の頻度が高すぎる呼び出しのオーバーヘッドを回避するためにまとめてれます。

  
## <a name="syntax"></a>構文  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 **int**の値、 **serverPreparedStatementDiscardThreshold**接続プロパティです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
