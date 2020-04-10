---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 203ed2f6a68e11af8c63157a850a146ea8d81464
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909595"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 **enablePrepareOnFirstPreparedStatementCall** 接続プロパティの値が返されます。 false の場合、最初の実行では sp_executesql が呼び出され、ステートメントは準備されません。2 回目が実行されると、sp_prepexec が呼び出され、準備されたステートメント ハンドルが実際に設定されます。 次の実行では sp_execute が呼び出されます。 そのため、ステートメントの実行が 1 回のみの場合、準備されたステートメントを閉じるときに sp_unprepare を行う必要はなくなります。 このオプションの既定値は、setDefaultEnablePrepareOnFirstPreparedStatementCall() を呼び出して変更することができます。

## <a name="syntax"></a>構文  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>戻り値
 **enablePrepareOnFirstPreparedStatementCall** 接続プロパティの値を含む**ブール値**です。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバー バージョン 6.4 以降で使用できます。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
