---
title: jdbcCompliant メソッド (SQLServerDriver) |Microsoft ドキュメント
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
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf5dc875f5f02ffd8e14ae00c738e71797c2b502
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>jdbcCompliant メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  あることを確認、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は JDBC 仕様に準拠していません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>戻り値  
 **true** JDBC ドライバーが最小要件を満たす場合です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 この jdbcCompliant メソッドは、java.sql.Driver インターフェイスの jdbcCompliant メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
