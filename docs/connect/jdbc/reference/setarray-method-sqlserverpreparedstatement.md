---
title: setArray メソッド (SQLServerPreparedStatement) |Microsoft ドキュメント
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
- SQLServerPreparedStatement.setArray
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7fb66d4-6a42-43d0-ba68-8514816917cb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 527d3722c6129510196c88ced4b5d61d8152dfc4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setarray-method-sqlserverpreparedstatement"></a>setArray メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された配列オブジェクトを指定されたパラメーターの数を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setArray(int i,  
                           java.sql.Array x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *私*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 配列オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setArray メソッドは、java.sql.PreparedStatement インターフェイスの setArray メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
