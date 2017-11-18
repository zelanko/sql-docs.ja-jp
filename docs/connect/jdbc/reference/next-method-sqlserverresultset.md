---
title: "次のメソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5fe62919bd765d83e2d3a38a9cdda33d88312e29
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="next-method-sqlserverresultset"></a>次のメソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルを現在の位置から 1 行下に移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**新しい現在の行が有効な場合です。 **false**がこれ以上行を処理する場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [次へ] このメソッドは、java.sql.ResultSet インターフェイスの次のメソッドによって指定されます。  
  
 結果セットのカーソルは、初期状態では先頭行よりも前にあります。 次のメソッドに最初の呼び出しによって、最初の行を現在の行は、2 つ目の呼び出しによって、現在の行を行し、2 つ目。  
  
 入力ストリームが現在の行の開いている場合は、次のメソッドの呼び出しは暗黙的に閉じられます。 警告チェーン、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)新しい行が読み取られるときに、オブジェクトをオフにします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

