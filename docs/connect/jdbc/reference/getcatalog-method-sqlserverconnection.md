---
title: getCatalog メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cc3aedba38d3ade6d08e1829d5970c2585cb1b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830507"
---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在のカタログ名を取得する[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**カタログ名を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCatalog メソッドは、java.sql.Connection インターフェイスの getCatalog メソッドによって指定されます。  
  
 設定されていない場合は、SQLServerConnection オブジェクト、または null の現在のカタログ プロパティを返します。 カタログ プロパティで明示的に設定されて、 [setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)メソッドを現在のカタログの TDS に対する環境変更を読み取ることによって暗黙的に更新します。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
