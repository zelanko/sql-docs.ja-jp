---
title: getCatalog メソッド (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 93cd6a4f612af7de32dc790f497a3d7a11b9cd1e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803978"
---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトの現在のカタログ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>戻り値  
 カタログ名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getCatalog メソッドは、java.sql.Connection インターフェイスの getCatalog メソッドによって指定されます。  
  
 設定されていない場合は、SQLServerConnection オブジェクト、または null の現在のカタログ プロパティを返します。 カタログ プロパティは、[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md) メソッドを使用して明示的に設定されるか、現在のカタログの TDS に対する環境変更を読み取って暗黙的に更新されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
