---
title: isNullable メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント
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
apiname:
- SQLServerResultSetMetaData.isNullable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c0fce3fe-5b16-4f60-9b0e-e9b30a90525e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d2ecec6231a666e9ac95060484b261fe85d5a0f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="isnullable-method-sqlserverresultsetmetadata"></a>isNullable メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列に null 値が許容されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int isNullable(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、列を null にすることができます。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isNullable メソッドは、java.sql.ResultSetMetaData インターフェイスの isNullable メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
