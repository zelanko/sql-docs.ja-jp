---
title: "rollback (java.sql.Savepoint) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.rollback (java.sql.Savepoint)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0b774454bdd981decb1a2f40be43550b2bdd3272
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="rollback-method-javasqlsavepoint"></a>rollback (java.sql.Savepoint) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  後で行われたすべての変更を元に戻します、指定された[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)オブジェクトを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *s*  
  
 ロールバックにセーブポイント オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このロールバック メソッドは、java.sql.Connection インターフェイスの rollBack メソッドによって指定されます。  
  
 このメソッドは、自動コミット モードが無効になっている場合にのみ使用してください。  
  
## <a name="see-also"></a>参照  
 [rollback メソッド & #40 です。SQLServerConnection &#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

