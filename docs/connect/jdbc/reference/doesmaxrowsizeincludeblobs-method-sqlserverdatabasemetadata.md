---
title: doesMaxRowSizeIncludeBlobs メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.doesMaxRowSizeIncludeBlobs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c90a7a7-5a59-4858-bb26-3e725d8611d7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2418bddf70809271600066e6cd517942b1cafa04
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata"></a>doesMaxRowSizeIncludeBlobs メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得の場合、戻り値の値かどうか、 [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md)メソッドには、SQL データ型 LONGVARCHAR と LONGVARBINARY が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean doesMaxRowSizeIncludeBlobs()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**戻り値には、データ型が含まれている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この doesMoxRowSizeIncludeBlobs メソッドは、java.sql.DatabaseMetaData インターフェイスの doesMoxRowSizeIncludeBlobs メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
