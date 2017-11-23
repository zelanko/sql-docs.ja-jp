---
title: "getUnicodeStream (java.lang.String) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.getUnicodeStream (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e8ea50a3-804a-4752-96e5-eb3d521f93c1
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 43211dd63c93716fee880950d244b9569fa2c618
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getunicodestream-method-javalangstring"></a>getUnicodeStream (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Unicode 文字のストリームとしてオブジェクト。  
  
> [!NOTE]  
>  このメソッドは、JDBC 仕様で推奨されていません。このメソッドを呼び出すと、"未実装" 例外がスローされます。 代わりに、使用する必要があります、 [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getUnicodeStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getUnicodeString メソッドは、java.sql.ResultSet インターフェイスの getUnicodeString メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getUnicodeStream メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
