---
title: "setWorkstationID メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 536a0b9dd7f047ae725bb03c45a5e3d8357a8f90
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setworkstationid-method-sqlserverdatasource"></a>setWorkstationID メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるコンピューター名、クライアントの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *workstationID*  
  
 A**文字列**クライアント コンピューター名を格納しています。  
  
## <a name="remarks"></a>解説  
 workstationID は、クライアント コンピューターまたはワークステーションの名前です。 WorkstationID プロパティが設定されていない場合、既定値は InetAddress.getLocalHost().getHostName() メソッドを呼び出すことによって構築されます。 GetHostName が空白の値を返す場合は、getHostAddress().toString() メソッドが呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

