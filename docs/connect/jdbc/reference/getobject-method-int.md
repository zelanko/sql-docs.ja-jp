---
title: getObject (int) メソッド |Microsoft ドキュメント
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
- SQLServerCallableStatement.getObject (jnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4b8366b-c065-48e1-b712-19e2d9834228
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 027c7c43798649986d7dffc705ef9bd003215b74
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getobject-method-int"></a>getObject (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値を Java プログラミング言語のオブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.Object getObject(int index)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **オブジェクト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getObject メソッドは、java.sql.CallableStatement インターフェイスの getObject メソッドによって指定されます。  
  
 このメソッドは、指定された列の値を Java オブジェクトとして返します。 この Java オブジェクトの型は、JDBC 仕様に指定されている組み込み型のマッピングに基づく、列の SQL 型に対応する既定の Java オブジェクト型です。 値が SQL NULL の場合、ドライバーは Java の null を返します。  
  
 このメソッドは、データベース固有の抽象データ型を読み取る場合にも使用できます。 JDBC 2.0 では、SQL ユーザー定義型のデータを具体化する getObject メソッドの動作が拡張されました。 呼び出しがある場合は、このメソッドの動作は、列には、構造化または個別の値が含まれている、`getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`です。  
  
 以降では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0。  
  
-   型の値**日付**java.sql.Date オブジェクトとして返されます。  
  
-   型の値**時間**java.sql.Time オブジェクトとして返されます。  
  
-   型の値**datetime2**の java.sql.Timestamp オブジェクトとして返されます。  
  
-   型の値**datetimeoffset**は microsoft.sql.DateTimeOffset オブジェクトとして返されます。  
  
## <a name="see-also"></a>参照  
 [getObject メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
