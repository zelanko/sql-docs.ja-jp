---
title: "getObjectInstance メソッド (SQLServerDataSourceObjectFactory) |Microsoft ドキュメント"
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
apiname: SQLServerDataSourceObjectFactory.getObjectInstance
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa9417d9b20ae5c1858c3c8f10019383565c4330
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getobjectinstance-method-sqlserverdatasourceobjectfactory"></a>getObjectInstance メソッド (SQLServerDataSourceObjectFactory)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定したデータ ソース オブジェクトのインスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ref*  
  
 **オブジェクト**値。  
  
 *name*  
  
 オブジェクトの名前。  
  
 *c*  
  
 指定した名前に関連するコンテキストです。  
  
 *h*  
  
 オブジェクトの作成に使用する環境です。  
  
## <a name="return-value"></a>戻り値  
 **オブジェクト**値。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getObjectInstance メソッドは、javax.naming.spi.ObjectFactory インターフェイスの getObjectInstance メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSourceObjectFactory のメソッド](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [SQLServerDataSourceObjectFactory のメンバー](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [SQLServerDataSourceObjectFactory クラス](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
