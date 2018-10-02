---
title: getRowIdLifetime メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65541bc857dfcdd7c55caa8e2e7d3831026c79e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731520"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>getRowIdLifetime メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL RowId データ型がサポートされているかどうかを示す状態を返します。 サポートされている場合は、RowId オブジェクトの有効期間を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>戻り値  
 RowIdLifetime オブジェクト。  
  
> [!NOTE]  
>  JDBC Driver version 2.0 リリースでは、このメソッドは、java.sql.RowIdLifetime.ROWID_UNSUPPORTED 値を返します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getRowIdLifetime メソッドは、java.sql.DatabaseMetaData インターフェイスで getRowIdLifetime メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
