---
title: setEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource) |Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 18cd626fb3eee4690d87dd40edd50e64a4dcd98e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779142"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>setEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  特定の接続のインスタンスの動作を指定します。 この構成が、準備されたステートメントの最初の実行が sp_executesql を呼び出すし、2 番目の実行が発生した後、ステートメントは準備は、false の場合は呼び出し sp_prepexec とセットアップ、準備されたステートメントでは実際に処理します。 次の実行は sp_execute を呼び出します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。  
## <a name="syntax"></a>構文  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 新しい値、 **enablePrepareOnFirstPreparedStatementCall**接続プロパティです。  

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
