---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection) |Microsoft ドキュメント
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
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7839e70a612a59cbf08b82e3453d53cc84abe9a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 値を返します**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。 最初の実行が sp_executesql を呼び出すし、準備は、false の場合は、2 つ目の実行が発生すると、ステートメントが sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際に設定します。 次の実行は sp_execute を呼び出します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。 このオプションの既定値は、呼び出し元 setDefaultEnablePrepareOnFirstPreparedStatementCall() で変更できます。

## <a name="syntax"></a>構文  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>戻り値
 A**ブール**の値を格納している**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
