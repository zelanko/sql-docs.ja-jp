---
title: "getClob (java.lang.String) メソッド |Microsoft ドキュメント"
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
- SQLServerCallableStatement.getClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ad871d09-ec43-4885-9067-20854b439b0c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9bb2a36c5fd39fa8f28f4d693278281a7756317
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getclob-method-javalangstring"></a>getClob (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーター名を指定、Java プログラミング言語の Clob オブジェクトとして指定された JDBC BLOB パラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Clob getClob(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーター名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 Clob オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getClob メソッドは、java.sql.CallableStatement インターフェイスの getClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getClob メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

