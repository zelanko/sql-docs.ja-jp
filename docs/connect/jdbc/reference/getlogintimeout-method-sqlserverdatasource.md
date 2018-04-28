---
title: getLoginTimeout メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ca310bbfa7b367f595ecf35ef92e9189ef323a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>getLoginTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  秒の数を返しますこれ[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトが接続を確立中に待機します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**を待機する秒数を表す値です。  
  
## <a name="remarks"></a>解説  
 アプリケーションがタイムアウト値を明示的に指定しない場合、このメソッドは既定値の 15 秒を返します。  
  
 この getLoginTimeout メソッドは、javax.sql.DataSource インターフェイスの getLoginTimeout メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
