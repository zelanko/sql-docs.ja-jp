---
title: setSQLXML メソッド (SQLServerCallableStatement) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcc2c813c0c2f52872938ae09134f20664c7097c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setsqlxml-method-sqlservercallablestatement"></a>setSQLXML メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された SQLXML オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 **文字列**パラメーターの名前を示すです。  
  
 *xmlObject*  
  
 パラメーターの値を含む SQLXML オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setSQLXML メソッドは、java.sql.CallableStatement インターフェイスの setSQLXML メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
