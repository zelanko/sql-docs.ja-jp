---
title: "getWorkstationID メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.getWorkstationID
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f246bdc08ac9486da5fb5bee00b32128f2092fa
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>getWorkstationID メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるクライアント コンピューターの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**クライアント コンピューター名を格納しています。  
  
## <a name="remarks"></a>解説  
 workstationID は、クライアント コンピューターまたはワークステーションの名前です。 WorkstationID プロパティが設定されていない場合、既定値は InetAddress.getLocalHost().getHostName() メソッドを呼び出すことによって構築されます。 GetHostName が空白の値を返す場合は、getHostAddress().toString() メソッドが呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
