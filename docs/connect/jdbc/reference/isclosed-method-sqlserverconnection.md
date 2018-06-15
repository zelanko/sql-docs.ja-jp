---
title: isClosed メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94028c26ce5f2a7d43db72f9874e37dc68ec6877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839837"
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが閉じられました。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**接続が閉じる場合**false**されていない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isClosed メソッドは、java.sql.Connection インターフェイスの isClosed メソッドによって指定されます。  
  
 呼び出された SQLServerConnection オブジェクトの状態を確認します。 場合、接続が閉じられて、[閉じる](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)メソッドが呼び出された、または特定の致命的なエラーが発生した場合。 このメソッドは**true**のみを呼び出す際 close メソッドが呼び出された後にします。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
