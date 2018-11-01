---
title: getNClob (java.lang.String) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14f32e68272dfc6dd8f26c5020d1e18a5e4e5d8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768850"
---
# <a name="getnclob-method-javalangstring"></a>getNClob (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の **NCLOB** パラメーターの値を Java プログラミング言語の NClob オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を含む**文字列**です。  
  
## <a name="return-value"></a>戻り値  
 ANClobobject します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getNClob メソッドは、java.sql.CallableStatement インターフェイスの getNClob メソッドで規定されています。  
  
 このメソッドがのみの取得をサポート**NCHAR**、 **NVARCHAR**、 **NTEXT**、および**XML**パラメーター。 これらのメソッドを他のデータ型のパラメーターで呼び出すと、例外が発生します。  
  
## <a name="see-also"></a>参照  
 [getNClob メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
