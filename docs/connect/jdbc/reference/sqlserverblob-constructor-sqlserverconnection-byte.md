---
title: "SQLServerBlob コンス トラクター (SQLServerConnection, byte) |Microsoft ドキュメント"
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
apiname: SQLServerConnection, byte[].SQLServerBlob
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b75ad63c8bbf1a928c8a464b3997713f4a6e582e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>SQLServerBlob コンス トラクター (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  新しいインスタンスを初期化、 [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)クラスの指定した場合、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトおよび**バイト**配列。  
  
> [!NOTE]  
>  このメソッドは、JDBC Driver Version 2.0 では推奨されていません。 代わりに、使用、 [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *接続*  
  
 SQLServerConnection オブジェクト。  
  
 *データ*  
  
 A**バイト**配列。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob コンス トラクター](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
