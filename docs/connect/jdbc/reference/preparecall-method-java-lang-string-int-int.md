---
title: "prepareCall (java.lang.String、int, int) メソッド |Microsoft ドキュメント"
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
- SQLServerConnection.prepareCall (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 04d36a25-7f95-4675-9690-4462671b3d67
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06e2dd2ed6da9d593a62f72d825c90abca256a88
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="preparecall-method-javalangstring-int-int"></a>prepareCall (java.lang.String, int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)を生成するオブジェクト[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)特定の種類および同時実行のオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int resultSetType,  
                                              int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
 *resultSetType*  
  
 **Int**結果セットの種類を示すです。  
  
 *resultSetConcurrency*  
  
 **Int**結果セットの同時実行の種類を示すです。  
  
## <a name="return-value"></a>戻り値  
 CallableStatement オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この prepareCall メソッドは、java.sql.Connection インターフェイスの prepareCall メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [prepareCall メソッド & #40 です。SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
