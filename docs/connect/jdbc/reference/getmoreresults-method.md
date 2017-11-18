---
title: "getMoreResults () メソッド |Microsoft ドキュメント"
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
- SQLServerStatement.getMoreResults ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8259b562590d21c57f0780260f50bf15032a7ead
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getmoreresults-method-"></a>getMoreResults () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この次の結果に移動[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final boolean getMoreResults()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**返された結果が結果セットである場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMoreResults メソッドは、java.sql.Statement インターフェイスの getMoreResults メソッドによって指定されます。  
  
 取得した現在開いている結果セットのオブジェクトを閉じ、getMoreResults メソッドを暗黙的に呼び出して、 [getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [getMoreResults メソッド & #40 です。SQLServerStatement &#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

