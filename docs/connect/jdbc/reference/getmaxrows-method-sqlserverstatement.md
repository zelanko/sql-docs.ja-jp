---
title: getMaxRows メソッド (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3af453b1e82984e06da41a03b289107d72d0ce88
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行の最大数を取得する、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されるオブジェクト[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを含めることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**制限がない場合は、行、または 0 の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxRows メソッドは、java.sql.Statement インターフェイスの getMaxRows メソッドによって指定されます。  
  
 この getMaxRows メソッドは、常に、動的カーソルのスクロール可能な 0 を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
