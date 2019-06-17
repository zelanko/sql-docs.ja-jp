---
title: supportsStoredFunctionsUsingCallSyntax メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0e5c0579-84b5-4717-b128-0bcd512f6022
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 053dab7055969b502a79e2e2d0250cdd98749fbe
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797302"
---
# <a name="supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata"></a>supportsStoredFunctionsUsingCallSyntax メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のデータベースがストアド プロシージャのエスケープ構文を使用したユーザー定義関数またはベンダー定義関数の呼び出しをサポートするかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsStoredFunctionsUsingCallSyntax()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsStoredFunctionsUsingCallSyntax メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsStoredFunctionsUsingCallSyntax メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
