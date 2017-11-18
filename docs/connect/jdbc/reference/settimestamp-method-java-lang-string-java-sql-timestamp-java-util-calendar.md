---
title: "setTimestamp メソッド タイムスタンプと予定表の値を |Microsoft ドキュメント"
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
- SQLServerCallableStatement.setTimestamp (java.lang.String, java.sql.Timestamp, java.util.Calendar))
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 09dca1f9-225a-4acb-9857-9a947e0829be
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d6e4c2ce26ae2a057f1b184311e31fbdb907e9ba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="settimestamp-method-javalangstring-javasqltimestamp-javautilcalendar"></a>setTimestamp (java.lang.String, java.sql.Timestamp, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された Calendar オブジェクトを使用して、指定されたパラメーターを、渡されたタイムスタンプの値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTimestamp(java.lang.String sCol,  
                         java.sql.Timestamp x,  
                         java.util.Calendar c)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *x*  
  
 タイムスタンプ オブジェクトです。  
  
 *c*  
  
 予定表オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setTimestamp メソッドは、java.sql.CallableStatement インターフェイスの setTimestamp メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setTimestamp メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

