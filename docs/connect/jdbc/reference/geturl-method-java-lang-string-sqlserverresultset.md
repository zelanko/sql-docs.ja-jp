---
title: "getURL (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.getURL (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 105a5319-0f4c-4d08-964b-cc52f8e28ec1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da21a4fcb8845f6790a9cc9b0642b37b131eeb36
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="geturl-method-javalangstring-sqlserverresultset"></a>getURL (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) URL オブジェクトとしてオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.net.URL getURL(java.lang.String sColumn)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sColumn*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 URL のオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getURL メソッドは、java.sql.ResultSet インターフェイスの getURL メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getURL メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
