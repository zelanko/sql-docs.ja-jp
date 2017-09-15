---
title: "supportsGetGeneratedKeys メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.supportsGetGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0e4659-14e7-4743-aed8-1768ee2b29dd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5f338b45c2bc8cd142f2db2acaffc53bdc4489a5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="supportsgetgeneratedkeys-method-sqlserverdatabasemetadata"></a>supportsGetGeneratedKeys メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ステートメントの実行後に自動生成キーを取得できるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsGetGeneratedKeys()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsGetGeneratedKeys メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsGetGeneratedKeys メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
