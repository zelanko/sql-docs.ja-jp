---
title: "setLoginTimeout メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e95a0377de7fe9a901f33b5913e70399b298aba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>setLoginTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  秒数を設定この[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトが接続を確立中に待機します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *loginTimeout*  
  
 **Int**を待機する秒数を表す値です。 0 は、タイムアウトが既定のシステム タイムアウトであることを示します。既定のシステム タイムアウトは、既定では 15 秒に指定されています。  
  
## <a name="remarks"></a>解説  
 この setLoginTimeout メソッドは、javax.sql.DataSource インターフェイスの setLoginTimeout メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
