---
title: "getPrecision メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerResultSetMetaData.getPrecision
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: de46c96e-6ad6-4946-883e-807123658500
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca52ca740162aee4072e4d389df72b613f765892
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getprecision-method-sqlserverresultsetmetadata"></a>getPrecision メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の小数点以下桁数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPrecision(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**列の有効桁数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getPrecision メソッドは、java.sql.ResultSetMetaData インターフェイスの getPrecision メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
