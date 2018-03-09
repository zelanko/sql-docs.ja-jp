---
title: "setServerPreparedStatementDiscardThreshold メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cbda72d00f8af453989e59f0591f519f872609c
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ServerPreparedStatementDiscardThreshold 接続プロパティの値を設定します。 この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 ときに、設定は、< = 1 unprepare アクション準備されたステートメントを閉じるには直ちに実行されます。 これらの呼び出しが頻繁すぎる sp_unprepare の呼び出しのオーバーヘッドを避けるためにまとめてバッチ処理 > 1 の値が設定されている場合
 
## <a name="syntax"></a>構文  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *serverPreparedStatementDiscardThreshold*  
  
 新しい値、 **serverPreparedStatementDiscardThreshold**接続プロパティです。  

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
