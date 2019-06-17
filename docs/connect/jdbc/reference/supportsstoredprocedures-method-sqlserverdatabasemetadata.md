---
title: supportsStoredProcedures メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsStoredProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 776ff53a-8bf3-4864-a7b7-170fdef1a87b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c1fec9c817e8671dd5d48f8c9d9fe13d611f864b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797305"
---
# <a name="supportsstoredprocedures-method-sqlserverdatabasemetadata"></a>supportsStoredProcedures メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースがストアド プロシージャのエスケープ構文を使用するストアド プロシージャの呼び出しをサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsStoredProcedures()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsStoredProcedures メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsStoredProcedures メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
