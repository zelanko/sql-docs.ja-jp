---
title: "setObject (int, java.lang.Object) メソッド |Microsoft ドキュメント"
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
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2116f0662e21e4cb38d60560a680e90e6b2321d9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setobject-method-int-javalangobject"></a>setObject (int, java.lang.Object) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたオブジェクトを使用して、指定されたパラメーターの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**パラメーター数を示すです。  
  
 *obj*  
  
 オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setObject メソッドは、java.sql.PreparedStatement インターフェイスの setObject メソッドによって指定されます。  
  
 この setObject メソッドを呼び出す前に、アプリケーションは、次のいずれかを使用して、指定されたパラメーターを設定する可能性があります。  
  
-   セット\<型 >、SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスのメソッド  
  
-   SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスの setNull メソッド  
  
-   [RegisterOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) SQLServerCallableStatement クラスのメソッド  
  
 このような場合、パラメーターの型が自動的に設定されます。 アプリケーションが、obj 値が NULL の場合は、この setObject メソッドを呼び出す場合、ドライバーは、パラメーターの型が以前に呼び出されたメソッドで設定されているいずれかであると見なします。  
  
 Obj 値が NULL、そのパラメーターの型情報を特定できない場合は、この setObject メソッド モジュールによって、データベースに送信する前に、指定されたパラメーターが CHAR に変換します。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="see-also"></a>参照  
 [setObject メソッド & #40 です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

