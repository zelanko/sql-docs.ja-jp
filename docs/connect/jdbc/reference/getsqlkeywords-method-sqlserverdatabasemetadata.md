---
title: getSQLKeywords メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLKeywords
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a2a0dfbb-11ec-429f-aea6-8f44148ebb8e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3010ba1e7c846f7da859fdf35ccef20b63e02aa3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660360"
---
# <a name="getsqlkeywords-method-sqlserverdatabasemetadata"></a>getSQLKeywords メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースの SQL キーワードであって、SQL92 キーワードではない、すべてのキーワードのコンマ区切りの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSQLKeywords()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**SQL キーワードを格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getSQLKeywords メソッドは、java.sql.DatabaseMetaData インターフェイスで getSQLKeywords メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
