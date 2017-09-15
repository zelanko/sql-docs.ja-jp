---
title: "getReference メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
- SQLServerDataSource.getReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 035149aed809ffd295ab53b4acf0f7fc41c59f7a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getreference-method-sqlserverdatasource"></a>getReference メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この参照を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>戻り値  
 参照オブジェクト。  
  
## <a name="remarks"></a>解説  
 この getReference メソッドは、javax.naming.Referenceable インターフェイスの getReference メソッドによって指定されます。  
  
 前のバージョン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、SQLServerDataSource オブジェクトの SQLServerDataSource.setTrustStorePassword が呼び出された場合、対応するパスワードが存在するために使用するオブジェクトを許可する、SQLServerDataSource.getReference から返されるオブジェクト追加の接続を行います。 JDBC Driver 3.0 では、SQLServerDataSource.getReference から返されたオブジェクトにパスワードを設定してから、そのオブジェクトとの接続を確立する必要があります。  
  
 また、SQLServerDataSource.setTrustStorePassword を設定してから、データ ソースのプロパティをバインドする場合は、SQLServerDataSource.setTrustStorePassword を呼び出してから接続を取得する必要があります。 例を次に示します。  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
