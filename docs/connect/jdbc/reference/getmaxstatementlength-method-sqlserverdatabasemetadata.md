---
title: getMaxStatementLength メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxStatementLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f45fcf45-b9e7-4d14-a90a-ebc542ac7755
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 205b939a870ede1a5a4a02fec81d73ea8dba073d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981986"
---
# <a name="getmaxstatementlength-method-sqlserverdatabasemetadata"></a>getMaxStatementLength メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースで SQL ステートメントに許容される最大文字数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getMaxStatementLength()  
```  
  
## <a name="return-value"></a>戻り値  
 許容される最大文字数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxStatementLength メソッドは、java.sql.DatabaseMetaData インターフェイスの getMaxStatementLength メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
