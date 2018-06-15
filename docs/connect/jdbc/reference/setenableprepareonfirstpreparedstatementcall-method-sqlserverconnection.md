---
title: setEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3377e4322a823c8eeba415395a910c6d45edd8d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842247"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>setEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 特定の接続のインスタンスの動作を指定します。 値は、false を指定する最初の実行が sp_executesql を呼び出すし、sp_prepexec を呼び出すが、準備されたステートメント ハンドルを実際に設定され、2 つ目の実行が発生したら、ステートメントを準備できません。 場合、 次の実行は sp_execute を呼び出します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。

## <a name="syntax"></a>構文  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 新しい値、 **enablePrepareOnFirstPreparedStatementCall**接続プロパティです。  
 
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
