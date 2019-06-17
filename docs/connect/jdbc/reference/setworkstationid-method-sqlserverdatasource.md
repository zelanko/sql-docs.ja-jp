---
title: setWorkstationID メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3b9b4dd4ce34dcc39148a2346fd729a8dfb6b87f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773221"
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>setWorkstationID メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるクライアント コンピューターの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *workstationID*  
  
 クライアント コンピューターの名前を含む **String** です。  
  
## <a name="remarks"></a>Remarks  
 workstationID は、クライアント コンピューターまたはワークステーションの名前です。 WorkstationID プロパティが設定されていない場合、既定値は InetAddress.getLocalHost().getHostName() メソッドを呼び出すことによって構築されます。 空白の値を返す getHostName getHostAddress().toString() メソッドが呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
