---
title: "setTime (int, java.sql.Time) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerPreparedStatement.setTime (int, java.sql.Time)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 1e3878dc-42fe-4fac-8fe3-22a7bd70c6da
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32a92278010b6cb653453556374a5347229beccd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="settime-method-int-javasqltime"></a>setTime (int, java.sql.Time) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された時刻の値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setTime(int n,  
                          java.sql.Time x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 Time オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setTime メソッドは、setTime、java.sql.PreparedStatement インターフェイスのメソッドでによって指定されます。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="see-also"></a>参照  
 [setTime メソッド &#40;です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
