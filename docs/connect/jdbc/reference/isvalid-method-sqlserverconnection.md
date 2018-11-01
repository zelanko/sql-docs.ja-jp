---
title: isValid メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 855a2fc8c6ff5a1cb9cee1db7504e0dd309113b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727450"
---
# <a name="isvalid-method-sqlserverconnection"></a>isValid メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトが閉じられておらず、有効であるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *timeout*  
  
 接続の検証が完了するのを待つ秒数を示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 接続が有効な場合は **true** です。接続が有効でないか、タイムアウトするまでに接続の有効性を特定できない場合は、**false** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この isValid メソッドは、java.sql.Connection インターフェイスで isValid メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
