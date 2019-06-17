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
manager: jroth
ms.openlocfilehash: 2868fb92161b5e3458e5c5e0dc72ebdef074b3e7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796323"
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
  
  
