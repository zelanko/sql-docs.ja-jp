---
title: "getClob (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
- SQLServerResultSet.getClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1de9804-1f27-4854-8985-3385fadcbebb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14c4d1a32bbb408a26f72329ec49d462d978f7ef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getclob-method-javalangstring-sqlserverresultset"></a>getClob (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語で Clob オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Clob getClob(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *colName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 Clob オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getClob メソッドは、java.sql.ResultSet インターフェイスの getClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getClob メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

