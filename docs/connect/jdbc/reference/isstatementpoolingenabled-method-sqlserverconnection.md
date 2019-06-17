---
title: isStatementPoolingEnabled メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isStatementPoolingEnabled
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6265aaf5121e50684e205b5d80199222b510f5d6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796336"
---
# <a name="isstatementpoolingenabled-method-sqlserverconnection"></a>isStatementPoolingEnabled メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 ステートメントのプールが有効になっているかどうか、またはこの接続ではなくを返します。

## <a name="syntax"></a>構文  
  
```  
  
public boolean isStatementPoolingEnabled()  
```  

## <a name="return-value"></a>戻り値
 A**ブール**かどうか、ステートメントのプールが有効になっているかどうかを示すフラグを格納しています。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
