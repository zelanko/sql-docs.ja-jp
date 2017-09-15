---
title: "getAutoCommit メソッド (SQLServerConnection) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.getAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e2c8ee804ede53953f531fe945da39c7c0667cae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# getAutoCommit メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の自動コミット モードを取得[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## 構文  
  
```  
  
public boolean getAutoCommit()  
```  
  
## 戻り値  
 **true**自動コミット モードが有効になっている場合**false**されていない場合。  
  
## 例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## 解説  
 この getAutoCommit メソッドは、java.sql.Connection インターフェイスの getAutoCommit メソッドによって指定されます。  
  
## 参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
