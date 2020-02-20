---
title: getDisableStatementPooling メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getDisableStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2da0a2f04fa90b2d25dbd68baf7b769d5afdcf8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983637"
---
# <a name="getdisablestatementpooling-method-sqlserverconnection"></a>getDisableStatementPooling メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 **disableStatementPooling** 接続プロパティの値が返されます。 この設定により、この接続に対してステートメント プーリングを有効にするかどうかを制御します。

## <a name="syntax"></a>構文  
  
```  
  
public boolean getDisableStatementPooling()  
```  

## <a name="return-value"></a>戻り値
 **disableStatementPooling** 接続プロパティの値を含む**ブール値**です。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバー バージョン 6.4 以降で使用できます。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
