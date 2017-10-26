---
title: "getSQLStateType メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6395cf4f457983cb7ac2540522deea5da93d9b78
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
  

