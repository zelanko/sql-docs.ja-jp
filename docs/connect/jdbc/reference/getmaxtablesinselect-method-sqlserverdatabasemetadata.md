---
title: getMaxTablesInSelect メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxTablesInSelect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f5291217-2a0c-4daa-9e39-9f348fc911f7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d125e9dad6d5c6f82ff177abdaced9d784295c11
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981925"
---
# <a name="getmaxtablesinselect-method-sqlserverdatabasemetadata"></a>getMaxTablesInSelect メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで SELECT ステートメントに許容される最大のテーブル数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxTablesInSelect()  
```  
  
## <a name="return-value"></a>戻り値  
 許容されるテーブル数の最大値を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxTablesInSelect メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxTablesInSelect メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
