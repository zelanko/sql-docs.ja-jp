---
title: getReference メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33a1b82b5855447df7e9b55c7506e87f6ffb8f2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825997"
---
# <a name="getreference-method-sqlserverdatasource"></a>getReference メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトへの参照が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>戻り値  
 参照オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 この getReference メソッドは、javax.naming.Referenceable インターフェイスの getReference メソッドによって指定されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 がリリースされる前は、SQLServerDataSource オブジェクトの SQLServerDataSource.setTrustStorePassword が呼び出された場合、対応するパスワードが、SQLServerDataSource.getReference から返されるオブジェクトに内包される形で開示され、結果、そのオブジェクトを使用することによって、別の接続を確立することが可能でした。 JDBC Driver 3.0 では、SQLServerDataSource.getReference から返されたオブジェクトにパスワードを設定してから、そのオブジェクトとの接続を確立する必要があります。  
  
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
  
  
