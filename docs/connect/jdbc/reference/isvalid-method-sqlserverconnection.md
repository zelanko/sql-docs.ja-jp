---
title: isValid メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c1e65ecb40137e0da2de7abd8b5d40e7e744752
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isvalid-method-sqlserverconnection"></a>isValid メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが閉じられていないは現在も有効です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timeout*  
  
 **Int**接続の検証を待機する秒数を指定します。  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、接続が無効です。**false**かどうか、接続が正しくないか、タイムアウトの有効期限が切れる前に、接続の有効性を決定することはできません。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isValid メソッドは、java.sql.Connection インターフェイスの isValid メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
