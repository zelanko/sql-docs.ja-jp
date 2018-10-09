---
title: getNString (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b351e999-85bf-498b-915a-f91d89134bce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8416de108cd4456599375f54c7afc0b4a5fefa8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730500"
---
# <a name="getnstring-method-javalangstring"></a>getNString (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された値を取得**NCHAR**、 **NVARCHAR**、または**LONGNVARCHAR** Java プログラミング言語の文字列としてパラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.lang.String getNString(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を含む**文字列**です。  
  
## <a name="return-value"></a>戻り値  
 AStringobject します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getLong メソッドは、java.sql.CallableStatement インターフェイスの getLong メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getString メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメソッド](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)  
  
  
