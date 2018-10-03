---
title: supportsAlterTableWithDropColumn メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsAlterTableWithDropColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 55a182c1-28e5-4d32-aeb1-166a8ac76758
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c9394408ef3fb421033df56ecbac87494acddba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668870"
---
# <a name="supportsaltertablewithdropcolumn-method-sqlserverdatabasemetadata"></a>supportsAlterTableWithDropColumn メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが列の削除で ALTER TABLE をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsAlterTableWithDropColumn()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsAlterTableWithDropColumn メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsAlterTableWithDropColumn メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
