---
title: "getQueryTimeout メソッド (SQLServerStatement) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.getQueryTimeout
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e186dba1f77d8b3c8062b91e33b80917a3e5c6af
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>getQueryTimeout メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  秒数を取得[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]が待つこの[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**制限がない場合は、JDBC ドライバーが待機する秒数または 0 の数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getQueryTimeout メソッドは、java.sql.Statement インターフェイスの getQueryTimeout メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
