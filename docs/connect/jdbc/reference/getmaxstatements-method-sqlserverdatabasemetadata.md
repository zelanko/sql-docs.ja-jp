---
title: "getMaxStatements メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.getMaxStatements
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 71d58431-b671-49c5-939a-f581d1fef7cd
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 710be054840b51c6b22def89d73d62fc2a0d5df7
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getmaxstatements-method-sqlserverdatabasemetadata"></a>getMaxStatements メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースの同時に開くことができるアクティブなステートメントの最大数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxStatements()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**アクティブなステートメントの最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxStatements メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxStatements メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
