---
title: "getFetchDirection メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ae039ccdc76cdc6117f502971feafe683f58b0d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
  

