---
title: "getGeneratedKeys メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 224930c0a364158033e0e30ccfe855f8b71579aa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>getGeneratedKeys メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これを実行した結果作成される自動生成キー取得[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>戻り値  
 結果セット オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getGeneratedKeys メソッドは、java.sql.Statement インターフェイスの getGeneratedKeys メソッドによって指定されます。  
  
 このメソッドを使用する方法の詳細については、次を参照してください。[自動生成キーを使用して](../../../connect/jdbc/using-auto-generated-keys.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

