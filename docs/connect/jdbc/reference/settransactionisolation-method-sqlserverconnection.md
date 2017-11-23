---
title: "setTransactionIsolation メソッド (SQLServerConnection) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.setTransactionIsolation
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30d2934189ef13fa3250e5a3b043a751d276acb6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="settransactionisolation-method-sqlserverconnection"></a>setTransactionIsolation メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このトランザクションの分離レベルを変更しようとしています。 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)に指定されたオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *レベル*  
  
 **Int**次の分離レベルのいずれかを含む値です。  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setTransactionIsolation メソッドは、java.sql.Connection インターフェイスの setTransactionIsolation メソッドによって指定されます。  
  
 トランザクションの実行中にこのメソッドが呼び出された場合、トランザクションはコミットされません。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
