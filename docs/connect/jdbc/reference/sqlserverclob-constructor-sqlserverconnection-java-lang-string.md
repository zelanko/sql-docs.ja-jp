---
title: "SQLServerClob のコンス トラクター (SQLServerConnection, java.lang.String) |Microsoft ドキュメント"
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
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 028d7d4803ff53f518067d869fa192512209d723
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>SQLServerClob (SQLServerConnection, java.lang.String) コンストラクター
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)クラスの指定した場合、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトおよびデータの文字列。  
  
> [!NOTE]  
>  このメソッドは、JDBC Driver Version 2.0 では推奨されていません。 代わりに、使用、 [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *接続*  
  
 SQLServerConnection オブジェクト。  
  
 *データ*  
  
 CLOB データです。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のコンス トラクター](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

