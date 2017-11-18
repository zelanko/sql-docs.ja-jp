---
title: "getBytes (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.getBytes (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ff617165-47f8-41c1-9c51-37ffc7714923
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba0880570009106ead7d9d3ea803e01b0b7d17fe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getbytes-method-javalangstring-sqlserverresultset"></a>getBytes (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**バイト**Java プログラミング言語の配列。  
  
## <a name="syntax"></a>構文  
  
```  
  
public byte[] getBytes(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 配列**バイト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBytes メソッドは、java.sql.ResultSet インターフェイスの getBytes メソッドによって指定されます。  
  
 このメソッドでは、サーバーからバイトの生データを読み取ることにより、すべての列を取得できます。 byte 配列が、サーバーに格納されている形式のまま、サーバーから直接返されます。  
  
 以前のバージョンので、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]、SQLServerResultSet.getBytes を使用してバイト配列間の変換と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型**日付**、**時間**、 **datetime2**、または**datetimeoffset**です。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [getBytes メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

