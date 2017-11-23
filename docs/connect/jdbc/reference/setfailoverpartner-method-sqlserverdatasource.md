---
title: "setFailoverPartner メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.setFailoverPartner
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7aa59563e6980ef29f3e53e19519b83bcac8d721
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>setFailoverPartner メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース ミラーリング構成のために使用されるフェールオーバー サーバーの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *サーバー名*  
  
 A**文字列**フェールオーバー サーバーの名前を格納しています。  
  
## <a name="remarks"></a>解説  
 このメソッドで設定された値は、プリンシパル サーバーへの初期接続に失敗した場合に使用されます。初期接続が行われた後は、この値は無視されます。 [SetDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)このメソッドと組み合わせてメソッドが使用もする必要がありますか、例外がスローされます。  
  
 フェールオーバー サーバーの名前を設定する場合、ドライバーではフェールオーバー サーバーのポート番号を指定することはできません。 ただし、呼び出し、 [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)メソッドおよび[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)メソッドを[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)メソッドはサポートされています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
