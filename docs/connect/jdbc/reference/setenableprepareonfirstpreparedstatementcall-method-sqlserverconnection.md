---
title: setEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e58e1a3814bd4fefda85f9ec525270923ef45dfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729920"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>setEnablePrepareOnFirstPreparedStatementCall Method (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 特定の接続のインスタンスの動作を指定します。 値は false の最初の実行が sp_executesql を呼び出すし、2 番目の実行発生 sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際に設定すると、ステートメントを準備できません。 場合、 次の実行は sp_execute を呼び出します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。

## <a name="syntax"></a>構文  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 新しい値、 **enablePrepareOnFirstPreparedStatementCall**接続プロパティです。  
 
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
