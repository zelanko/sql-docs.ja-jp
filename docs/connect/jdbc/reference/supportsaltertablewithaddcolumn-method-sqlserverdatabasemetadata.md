---
title: supportsAlterTableWithAddColumn メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsAlterTableWithAddColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bbac1370-fbf6-4450-8599-4ed3b4db3fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88c3cf32648145f5673e2d353fead82cbe691258
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915638"
---
# <a name="supportsaltertablewithaddcolumn-method-sqlserverdatabasemetadata"></a>supportsAlterTableWithAddColumn メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが列の追加で ALTER TABLE をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsAlterTableWithAddColumn()  
```  
  
## <a name="return-value"></a>戻り値  
 サポートされている場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsAlterTableWithAddColumn メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsAlterTableWithAddColumn メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
