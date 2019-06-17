---
title: supportsCatalogsInTableDefinitions メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInTableDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e1e50ac-f3d4-416a-8a69-d8b7b4f30bf3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f80dad51a9ce9d0c156dbac86284372848fdcae9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66766397"
---
# <a name="supportscatalogsintabledefinitions-method-sqlserverdatabasemetadata"></a>supportsCatalogsInTableDefinitions メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  テーブル定義ステートメントでカタログ名を使用できるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsCatalogsInTableDefinitions()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この supportsCatalogsInTableDefinitions メソッドは、java.sql.DatabaseMetaData インターフェイスで supportsCatalogsInTableDefinitions メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
