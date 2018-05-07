---
title: setTime メソッドに時間と予定表の値 |Microsoft ドキュメント
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
- SQLServerCallableStatement.setTime (java.lang.String, java.lang.Time, java.lang.Calendar))
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ca08fea8-ee1a-49e4-a973-2923d325df79
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d53716c942a1c4bf5703316b0d0a8d760f6af3f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="settime-method-javalangstring-javasqltime-javautilcalendar"></a>setTime (java.lang.String, java.sql.Time, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された Calendar オブジェクトを使用して、指定されたパラメーターを、渡された時刻の値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTime(java.lang.String sCol,  
                    java.sql.Time x,  
                    java.util.Calendar c)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *x*  
  
 Time オブジェクト。  
  
 *c*  
  
 予定表オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setTime メソッドは、setTime、java.sql.CallableStatement インターフェイスのメソッドでによって指定されます。  
  
 以降で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 では、このメソッドの動作は、によって変更が、 **sendTimeAsDatetime**接続プロパティ ([接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)) および[SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)です。  
  
 詳細については、次を参照してください。[を構成する方法の java.sql.Time 値は、サーバーに送信される](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)です。  
  
## <a name="see-also"></a>参照  
 [setTime メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
