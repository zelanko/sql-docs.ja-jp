---
title: "getFetchSize メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
- SQLServerStatement.getFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8115ca58-8ae9-46ce-8515-7905d7bb25fe
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: efb6e1aca84c36afbfb761813ae8ab0efdfd2501
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getfetchsize-method-sqlserverstatement"></a>getFetchSize メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  結果の数のセットの結果セットから生成されたオブジェクトの既定のフェッチ サイズである行を取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getFetchSize()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**によって指定されるフェッチ サイズを示す、 [setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)メソッドです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getFetchSize メソッドは、java.sql.Statement インターフェイスの getFetchSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
