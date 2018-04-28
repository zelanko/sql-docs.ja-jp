---
title: getTableName メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント
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
- SQLServerResultSetMetaData.getTableName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a077b50-cc5a-4301-9398-49ea68544e89
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9332f0d03cc970c350eb9b042dd552e16fbb899
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettablename-method-sqlserverresultsetmetadata"></a>getTableName メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列のテーブル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getTableName(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**テーブル名を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTableName メソッドは、java.sql.ResultSetMetaData インターフェイスの getTableName メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
