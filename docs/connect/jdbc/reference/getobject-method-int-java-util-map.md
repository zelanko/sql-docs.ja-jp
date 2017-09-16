---
title: "getObject (int, java.util.Map) メソッド |Microsoft ドキュメント"
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
- SQLServerCallableStatement.getObject (int, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 164532be-7ed6-40fa-a273-dece4c8d72c4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 71de96500026936d5f734101d3e3712401ea7ac7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getobject-method-int-javautilmap"></a>getObject (int, java.util.Map) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  特定のマップ オブジェクトを使用して Java プログラミング言語パラメーター インデックス内のオブジェクトとして指定されたパラメーターの値を取得します。  
  
> [!NOTE]  
>  このメソッドは現在サポートされていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを使用すると、常に既定のマッピングが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.Object getObject(int index,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
 *マップ*  
  
 マップ オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 **オブジェクト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getObject メソッドは、java.sql.CallableStatement インターフェイスの getObject メソッドによって指定されます。  
  
 このメソッドは、指定された列の値を Java オブジェクトとして返します。 この Java オブジェクトの型は、JDBC 仕様に指定されている組み込み型のマッピングに基づく、列の SQL 型に対応する既定の Java オブジェクト型です。 値が SQL NULL の場合、ドライバーは Java の null を返します。  
  
 このメソッドは、データベース固有の抽象データ型を読み取る場合にも使用できます。 JDBC 2.0 API では、SQL ユーザー定義型のデータを具体化する getObject メソッドの動作が拡張されます。 呼び出しがある場合は、このメソッドの動作は、列には、構造化または個別の値が含まれている、`getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`です。  
  
 以降では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0。  
  
-   date 型の値は java.sql.Date オブジェクトとして返されます。  
  
-   time 型の値は java.sql.Time オブジェクトとして返されます。  
  
-   datetime2 型の値は java.sql.Timestamp オブジェクトとして返されます。  
  
-   datetimeoffset 型の値は microsoft.sql.DateTimeOffset オブジェクトとして返されます。  
  
## <a name="see-also"></a>参照  
 [getObject メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
