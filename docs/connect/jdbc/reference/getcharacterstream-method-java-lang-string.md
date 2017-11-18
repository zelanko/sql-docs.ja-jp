---
title: "getCharacterStream (java.lang.String) メソッド |Microsoft ドキュメント"
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
- SQLServerResultSet.getCharacterStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cdddc572-05c1-480d-b3e5-28270001575c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a882e903e689f67db7adf9b8d71d34851affd5b4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getcharacterstream-method-javalangstring"></a>getCharacterStream (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを java.io.Reader オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.ResultSet インターフェイスの getCharacterStream メソッドによって指定されます。  
  
 このメソッドは読み取り専用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]nchar、nvarchar、nvarchar (max)、および ntext などの Unicode 文字データ型。 ASCII 文字型などのその他のデータ型では、例外がスローされます。 ASCII データ型を読み取り、使用、 [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

