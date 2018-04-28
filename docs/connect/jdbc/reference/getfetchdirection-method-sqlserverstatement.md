---
title: getFetchDirection メソッド (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f21cbe1c98e24e38e1bbdaa236471d2d16d790f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>getFetchDirection メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これから生成される結果セットの既定値は、データベース テーブルから行をフェッチの方向を取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
> [!NOTE]  
>  このメソッドは現在実装されていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 そのため、このメソッドは常に FETCH_UNKNOWN を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**によって指定されるフェッチ方向を示す、 [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)メソッドです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getFetchDirection メソッドは、java.sql.Statement インターフェイスの getFetchDirection メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
