---
title: refreshRow メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
ms.topic: article
apiname:
- SQLServerResultSet.refreshRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac098d125e1ae2f599a2e68ab41a5de6439163b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="refreshrow-method-sqlserverresultset"></a>refreshRow メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース内の最新の値を使用して、現在の行を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この refreshRow メソッドは、java.sql.ResultSet インターフェイスの refreshRow メソッドによって指定されます。  
  
 カーソルが挿入行にあるときは、このメソッドを呼び出すことができません。  
  
 アプリケーションでこのメソッドを使用すると、データベースから行を再フェッチするよう、JDBC ドライバーに明示的に指示できます。 アプリケーションは、このメソッドを呼び出す必要があるときに、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]がキャッシュまたはプレフェッチをデータベースから行の最新の値を取得します。 フェッチ サイズが 1 よりも大きい場合、JDBC ドライバーが複数行を同時に更新することがあります。  
  
 すべての値は、トランザクション分離レベルとカーソルの応答性に応じて再フェッチされます。 Updater メソッドを呼び出した後、呼び出す前に、このメソッドが呼び出された場合、 [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)メソッド、行に対する更新が失われます。 このメソッドを頻繁に呼び出すと、パフォーマンスが低下することがあります。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
