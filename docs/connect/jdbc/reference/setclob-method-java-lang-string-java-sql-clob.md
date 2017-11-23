---
title: "setClob (java.lang.String, java.sql.Clob) メソッド |Microsoft ドキュメント"
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
ms.assetid: 256b5f55-7a6d-44fb-9a09-19fa39f19c35
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa4c66ef6d15e104d235a7df8cc16d9c8e4d986d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setclob-method-javalangstring-javasqlclob"></a>setClob (java.lang.String, java.sql.Clob) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された Clob オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.sql.Clob x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *x*  
  
 Clob オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClob メソッドは、java.sql.CallableStatement インターフェイスの setClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setClob メソッド &#40;です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
