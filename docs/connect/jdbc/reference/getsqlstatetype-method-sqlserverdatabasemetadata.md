---
title: "getSQLStateType メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.getSQLStateType
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dce25152f13c146261da11f03f4d26ba6a134bf1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>getSQLStateType メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQLException.getSQLState メソッドによって返される SQLSTATE が、X/Open (現在は Open Group)、SQL CLI、SQL99 (JDBC 3.0)、SQL:2003 (JDBC 4.0) のいずれであるかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**を示す、SQLSTATE の種類を次の値のいずれかを指定することができます。  
  
-   Java ランタイム環境バージョン 5.0: 場合、 **xopenStates**接続プロパティに設定**true**DatabaseMetaData.sqlStateXOpen を返します。 それ以外の場合、DatabaseMetaData.sqlStateSQL99 です。  
  
-   Java ランタイム環境バージョン 6.0: 場合、 **xopenStates**接続プロパティに設定**true**DatabaseMetaData.sqlStateXOpen を返します。 それ以外の場合、DatabaseMetaData.sqlStateSQL です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLStateType メソッドは、java.sql.DatabaseMetaData インターフェイスの getSQLStateType メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
