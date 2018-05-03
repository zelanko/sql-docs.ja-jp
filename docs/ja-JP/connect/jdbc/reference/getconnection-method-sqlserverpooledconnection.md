---
title: getConnection メソッド (SQLServerPooledConnection) |Microsoft ドキュメント
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
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.getConnection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 05bdb61f-26e8-480f-a1c1-1e46a8ed4b70
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62d6078aadeca958204c8c50201d398e179e0f56
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getconnection-method-sqlserverpooledconnection"></a>getConnection メソッド (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  物理的な接続用のオブジェクト ハンドルを作成これ[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)オブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>戻り値  
 接続オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この getConnection メソッドは、javax.sql.PooledConnection インターフェイスの getConnection メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerPooledConnection メソッド](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection のメンバー](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection クラス](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
