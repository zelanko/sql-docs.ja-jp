---
title: "setAutoCommit メソッド (SQLServerConnection) |Microsoft ドキュメント"
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
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1549693ac6b4e558c2fc86b29dc6aaa6122c235
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# setAutoCommit メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  自動コミット モードを設定[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトを特定の状態にします。  
  
## 構文  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### パラメーター  
 *value*  
  
 **true** 、接続の自動コミット モードを有効にする**false**を無効にします。  
  
## 例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## 解説  
 この setAutoCommit メソッドは、java.sql.Connection インターフェイスの setAutoCommit メソッドによって指定されます。  
  
 自動コミット モードの接続では、SQL ステートメントはすべて個別のトランザクションとして実行され、コミットされます。 それ以外の場合、SQL ステートメントはいずれかへの呼び出しで終了するトランザクションにグループ化、[コミット](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)メソッドまたは[ロールバック](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)メソッドです。 既定では、新しい接続は自動コミット モードとなります。  
  
 コミットは、ステートメントの実行が終了するか、次のステートメントの実行が開始されると発生します。 返すステートメントの場合、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを結果セットの最後の行が取得されたとき、または結果セットが閉じられたときにステートメントが完了します。 高度なケースでは、単一のステートメントが、出力パラメーターの値以外に複数の結果を返すことがあります。 このような場合、コミットは、すべての結果および出力パラメーターの値が取得されると発生します。  
  
 自動コミット モードが場合**false**、JDBC ドライバーは、各コミット後の新しいトランザクションに暗黙的に開始されます。  
  
> [!NOTE]  
>  トランザクションの実行中にこのメソッドが呼び出された場合、トランザクションはコミットされます。  
  
## 参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
