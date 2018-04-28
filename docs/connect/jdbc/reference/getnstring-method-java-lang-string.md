---
title: getNString (java.lang.String) メソッド |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: b351e999-85bf-498b-915a-f91d89134bce
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8731943db3bcfeb9ddc1f12f307114a5abad6781
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getnstring-method-javalangstring"></a>getNString (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された値を取得**NCHAR**、 **NVARCHAR**、または**LONGNVARCHAR** Java プログラミング言語の文字列としてのパラメーターです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.lang.String getNString(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーター名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 AStringobject です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getNString メソッドは、java.sql.CallableStatement インターフェイスの getNString メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getNString メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメソッド](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)  
  
  
