---
title: setNClob (java.lang.String, java.sql.NClob) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4e30d242-0c1b-45db-b75f-41b041692f31
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5c466c4c27f49328644e89b2161f47db965c895
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setnclob-method-javalangstring-javasqlnclob"></a>setNClob (java.lang.String, java.sql.NClob) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定した NClob オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *value*  
  
 NClob オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 このメソッドを使用する必要があります**NCHAR**、 **NVARCHAR**、 **NTEXT**、および**XML**パラメーターのデータ型。  
  
 この setNClob メソッドは、java.sql.CallableStatement インターフェイスの setNClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setNClob メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
