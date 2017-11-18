---
title: "getBigDecimal (java.lang.String, int) メソッド |Microsoft ドキュメント"
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
- SQLServerCallableStatement.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6967ba55-9c9a-4f6f-a4d2-8ee9c9a82c14
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f47ef135f367e5263616aec8a29cd3693967974
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring-int"></a>getBigDecimal (java.lang.String, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡された名前と小数点以下桁数を使用して、指定されたパラメーターの値を java.math.BigDecimal として取得します。  
  
> [!NOTE]  
>  このメソッドは、JDBC 仕様では推奨されていません。 代わりに、使用する必要があります、 [getBigDecimal (java.lang.String)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String sCol,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *scale*  
  
 **Int**小数点の右側にある数字の数を示すです。  
  
## <a name="return-value"></a>戻り値  
 BigDecimal オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBigDecimal メソッドは、java.sql.CallableStatement インターフェイスの getBigDecimal メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getBigDecimal メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

