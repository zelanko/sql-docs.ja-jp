---
title: setDateTimeOffset メソッド (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 264de7ac150aca7494a380fbbd4f5b490607c5c6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974645"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>setDateTimeOffset メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドは [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 指定された列の値が [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値に設定されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 列の名前。  
  
 *t*  
  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md) オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [SQLServerCallableStatement.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md) を使用して [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値を取得できます。  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) は列の序数を受け取ります。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
