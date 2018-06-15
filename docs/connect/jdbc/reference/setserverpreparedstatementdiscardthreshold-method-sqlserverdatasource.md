---
title: setServerPreparedStatementDiscardThreshold メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a0105f615a123aa9ec4a4d329601c7992f76469
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845237"
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
  
  
