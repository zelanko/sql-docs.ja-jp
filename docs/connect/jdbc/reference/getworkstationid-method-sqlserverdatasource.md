---
title: getWorkstationID メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98cde4953d60f13d1768b06dbfab9ada6ea8af55
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978050"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>getWorkstationID メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるクライアント コンピューターの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>戻り値  
 クライアント コンピューターの名前を含む **String** です。  
  
## <a name="remarks"></a>解説  
 workstationID は、クライアント コンピューターまたはワークステーションの名前です。 workstationID プロパティが設定されていない場合、既定値は InetAddress.getLocalHost().getHostName() メソッドを呼び出して構成されます。 getHostName によって空白の値が返された場合は、getHostAddress().toString() メソッドが呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
