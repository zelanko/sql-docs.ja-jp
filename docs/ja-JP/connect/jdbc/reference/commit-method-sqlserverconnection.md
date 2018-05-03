---
title: commit メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8999c0bf7a7be89cead090bbbfd4d2ae767217a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="commit-method-sqlserverconnection"></a>commit メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  前回のコミットまたはロールバック以降を恒久的に、すべての変更が行われ、これによって現在保持されているデータベース ロックは解放[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このコミット メソッドは、java.sql.Connection インターフェイスの commit メソッドによって指定されます。  
  
 このメソッドは、自動コミット モードが無効になっている場合にのみ使用してください。  
  
 クライアントが手動トランザクションを開始した後、SQL Server が何らかの理由でその手動トランザクションをロールバックした場合、このメソッドは失敗して例外をスローすることに注意してください。 など、クライアントが明示的に ROLLBACK TRANSACTION を呼び出すストアド プロシージャを呼び出した場合、例外がスローされ、クライアントが、commit メソッドを呼び出します。 さらに、SQL Server をロールバックするための十分な重要度 (16 以上のエラーが発生した場合、クライアントが開始した手動トランザクションです。後続の呼び出し、commit メソッドに例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
