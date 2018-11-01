---
title: executeQuery (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d266af1e09c457db4742d6aca06df65acfd505a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774375"
---
# <a name="executequery-method-javalangstring"></a>executeQuery (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL ステートメントを実行し、1 つの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを格納しています。  
  
## <a name="return-value"></a>戻り値  
 SQLServerResultSet オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この executeQuery メソッドは、java.sql.Statement インターフェイスの executeQuery メソッドで規定されています。  
  
 このメソッドは、[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) クラスで見つかる [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドをオーバーライドします。  
  
 SQLServerPreparedStatement オブジェクトが作成される際、オブジェクトの SQL ステートメントが指定されるため、このメソッドを呼び出すと例外が発生します。  
  
 渡された SQL ステートメントによって 1 つの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクト以外のものが生成された場合は、[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) がスローされます。  
  
## <a name="see-also"></a>参照  
 [executeQuery メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
