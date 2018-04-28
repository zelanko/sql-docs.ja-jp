---
title: getRowIdLifetime メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 492f2064623dceefdc45d8e38f4a0b49294e7aff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>getRowIdLifetime メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL RowId データ型がサポートされているかどうかを示す状態を返します。 サポートされている場合は、RowId オブジェクトの有効期間を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>戻り値  
 RowIdLifetime オブジェクトです。  
  
> [!NOTE]  
>  JDBC Driver version 2.0 リリースでは、このメソッドは、java.sql.RowIdLifetime.ROWID_UNSUPPORTED 値を返します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getRowIdLifetime メソッドは、java.sql.DatabaseMetaData インターフェイスの getRowIdLifetime メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
