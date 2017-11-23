---
title: "position (java.sql.Clob, long) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerClob.position (java.sql.Clob, long)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b2fb34d5-1d34-4764-a795-712d9c6aa313
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0b74694d54955cc484f9858aaa6194c733b0295
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="position-method-javasqlclob-long"></a>position (java.sql.Clob, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された開始位置に基づいて、CLOB 内の指定された CLOB オブジェクトの文字位置を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long position(java.sql.Clob searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *searchstr*  
  
 検索する部分文字列です。  
  
 *開始*  
  
 検索を開始する位置です。 最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 部分文字列が現れる位置です。部分文字列がない場合は -1 が返されます。 最初の位置は 1 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この位置メソッドは、位置、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を配置します。SQLServerClob &#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
