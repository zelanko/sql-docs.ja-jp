---
title: createStatement (int、int, int) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a98b5be003546b2573a1ecb844d4c5a08c7f6913
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="createstatement-method-int-int-int"></a>createStatement (int, int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)を生成するオブジェクト[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)特定の種類、同時実行性、および保持機能を持つオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *resultSetType*  
  
 **Int**結果を表す値が型を設定します。  
  
 *nConcur*  
  
 **Int**結果を表す値は、同時実行の種類を設定します。  
  
 *nHold*  
  
 **Int**保持機能を表す値です。  
  
## <a name="return-value"></a>戻り値  
 ステートメントのオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この createStatement メソッドは、java.sql.Connection インターフェイスの createStatement メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [createStatement メソッド&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
