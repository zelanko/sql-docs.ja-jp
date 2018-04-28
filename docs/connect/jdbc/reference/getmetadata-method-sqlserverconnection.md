---
title: getMetaData メソッド (SQLServerConnection) |Microsoft ドキュメント
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
- SQLServerConnection.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86223cb5-3bf4-489a-8c82-669a91764f2b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b31864053741474597164a7b5455917a37803772
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getmetadata-method-sqlserverconnection"></a>getMetaData メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得、 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)先であるデータベースについてのメタデータを格納しているオブジェクト[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが接続を表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.DatabaseMetaData getMetaData()  
```  
  
## <a name="return-value"></a>戻り値  
 DatabaseMetaData オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMetaData メソッドは、java.sql.Connection インターフェイスの getMetaData メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
