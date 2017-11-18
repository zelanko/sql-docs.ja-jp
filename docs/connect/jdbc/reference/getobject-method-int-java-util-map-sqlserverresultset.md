---
title: "getObject (int, java.util.Map) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.getObject (int, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df85a514-ab43-4bf6-98dd-f7f37fad1850
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7e81bc8402185d549c438edfdb612b2776f881c0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getobject-method-int-javautilmap-sqlserverresultset"></a>getObject (int, java.util.Map) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを java プログラミング言語を特定のマップ オブジェクトを使用して、オブジェクトとして。  
  
> [!NOTE]  
>  このメソッドは現在サポートされていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを使用すると、常に既定のマッピングが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.Object getObject(int i,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *私*  
  
 **Int**列インデックスを示すです。  
  
 *マップ*  
  
 マップ オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 **オブジェクト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getObject メソッドは、java.sql.ResultSet インターフェイスの getObject メソッドによって指定されます。  
  
 このメソッドは、指定された列の値を Java オブジェクトとして返します。 この Java オブジェクトの型は、JDBC 仕様に指定されている組み込み型のマッピングに基づく、列の SQL 型に対応する既定の Java オブジェクト型です。 値が SQL NULL の場合、ドライバーは Java の null を返します。  
  
 このメソッドは、データベース固有の抽象データ型を読み取る場合にも使用できます。 JDBC 2.0 API では、SQL ユーザー定義型のデータを具体化する getObject メソッドの動作が拡張されます。 呼び出しがある場合は、このメソッドの動作は、列には、構造化または個別の値が含まれている、`getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`です。  
  
 以降では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0。  
  
-   date 型の値は java.sql.Date オブジェクトとして返されます。  
  
-   time 型の値は java.sql.Time オブジェクトとして返されます。  
  
-   datetime2 型の値は java.sql.Timestamp オブジェクトとして返されます。  
  
-   datetimeoffset 型の値は microsoft.sql.DateTimeOffset オブジェクトとして返されます。  
  
## <a name="see-also"></a>参照  
 [getObject メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

