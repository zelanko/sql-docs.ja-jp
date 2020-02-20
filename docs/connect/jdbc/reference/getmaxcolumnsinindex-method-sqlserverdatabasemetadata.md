---
title: getMaxColumnsInIndex メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInIndex
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 108f0e2c-7dc5-4195-8248-0758a75a314e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f98d3bdb5e893d1c120be059e1ad1de446dc8d6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67982253"
---
# <a name="getmaxcolumnsinindex-method-sqlserverdatabasemetadata"></a>getMaxColumnsInIndex メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースでインデックスに許容される最大の列数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxColumnsInIndex()  
```  
  
## <a name="return-value"></a>戻り値  
 許容される最大の列数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxColumnsInIndex メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxColumnsInIndex メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
