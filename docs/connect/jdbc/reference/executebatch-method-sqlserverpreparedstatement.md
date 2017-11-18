---
title: "executeBatch メソッド (SQLServerPreparedStatement) |Microsoft ドキュメント"
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
- SQLServerPreparedStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c339a53bd782047db67bc58a61283ce9cd4cbe9e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executebatch-method-sqlserverpreparedstatement"></a>executeBatch メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  実行するコマンド バッチをデータベースに送信します。 すべてのコマンドが正常に実行されている場合は、更新数の配列が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>戻り値  
 更新数を含む int 配列です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>解説  
 この executeBatch メソッドは、java.sql.Statement インターフェイスの executeBatch メソッドによって指定されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 はストアド プロシージャが OUT または INOUT を受け入れる場合に (PreparedStatement から継承) CallableStatement.executeBatch メソッドへの呼び出しが、BatchUpdateException をスローするという JDBC 4.0 の勧告に準拠しています。パラメーターにも更新数の何か以外を返します。  
  
 このメソッドは[、sqlserverstatement.executebatch をオーバーライド](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

