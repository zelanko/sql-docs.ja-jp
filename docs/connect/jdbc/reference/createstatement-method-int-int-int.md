---
title: "createStatement (int、int, int) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0298571db91e5f733de531f1ff30de88c457b5f7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
 [createStatement メソッド & #40 です。SQLServerConnection &#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
