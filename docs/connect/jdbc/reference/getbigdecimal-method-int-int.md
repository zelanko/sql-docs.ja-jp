---
title: "getBigDecimal (int, int) メソッド |Microsoft ドキュメント"
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
- SQLServerCallableStatement.getBigDecimal (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d9351b35-7046-4852-a612-72d4c46b2bbb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 492e404743fdcd43b08f08fbdbcccb51810a30f3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-int-int"></a>getBigDecimal (int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスと小数点以下桁数を使用して、指定されたパラメーターの値を java.math.BigDecimal として取得します。  
  
> [!NOTE]  
>  このメソッドは、JDBC 仕様では推奨されていません。 代わりに、使用する必要があります、 [getBigDecimal (int)](../../../connect/jdbc/reference/getbigdecimal-method-int.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.math.BigDecimal getBigDecimal(int index,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
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
  
  
