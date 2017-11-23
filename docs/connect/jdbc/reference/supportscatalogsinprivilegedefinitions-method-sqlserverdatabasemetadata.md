---
title: "supportsCatalogsInPrivilegeDefinitions メソッド |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.supportsCatalogsInPrivilegeDefinitions
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: cc18f99e-c19f-4bd0-96ae-b9a6a0de1926
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65c45b6032c3317a0433e69adc2ad5d983bda78c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="supportscatalogsinprivilegedefinitions-method-sqlserverdatabasemetadata"></a>supportsCatalogsInPrivilegeDefinitions メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  特権定義ステートメントでカタログ名を使用できるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsCatalogsInPrivilegeDefinitions()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsCatalogsInPrivilegeDefinitions メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsCatalogsInPrivilegeDefinitions メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
