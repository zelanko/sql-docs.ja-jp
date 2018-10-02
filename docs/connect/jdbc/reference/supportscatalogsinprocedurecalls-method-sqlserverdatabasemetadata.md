---
title: supportsCatalogsInProcedureCalls メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInProcedureCalls
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ec3571a-c7c6-4b94-a9ea-ac08adc7f978
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b8bd175c5094ea284b98ca50f5e029280eb6158
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637400"
---
# <a name="supportscatalogsinprocedurecalls-method-sqlserverdatabasemetadata"></a>supportsCatalogsInProcedureCalls メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  プロシージャ呼び出しステートメントでカタログ名を使用できるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsCatalogsInProcedureCalls()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsCatalogsInProcedureCalls メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsCatalogsInProcedureCalls メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
