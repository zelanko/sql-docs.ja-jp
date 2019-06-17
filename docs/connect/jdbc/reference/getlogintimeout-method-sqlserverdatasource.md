---
title: getLoginTimeout メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ec8d033bc6d9bc451eaa606a00881bd4e533aa97
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66793164"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>getLoginTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続の試行中に [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) オブジェクトが待機する秒数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 待機する秒数を表す **int** 値です。  
  
## <a name="remarks"></a>Remarks  
 アプリケーションがタイムアウト値を明示的に指定しない場合、このメソッドは既定値の 15 秒を返します。  
  
 この getLoginTimeout メソッドは、javax.sql.DataSource インターフェイスで getLoginTimeout メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
