---
title: "insertRow メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9297b57b1ad4ded2611fadb1034a61046e3a4d25
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="insertrow-method-sqlserverresultset"></a>insertRow メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これを挿入行の内容を追加[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトと、データベースにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この insertRow メソッドは、java.sql.ResultSet インターフェイスの insertRow メソッドによって指定されます。  
  
 このメソッドを呼び出すときに、カーソルが挿入行にある必要があります。 このメソッドが呼び出された後も、カーソルは挿入行に残り、結果セットは挿入モードのままになります。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

