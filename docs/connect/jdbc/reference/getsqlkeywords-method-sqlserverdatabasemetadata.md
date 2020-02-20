---
title: getSQLKeywords メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
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
ms.openlocfilehash: 79995b672219c456284809ee16593fbe800a9638
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979742"
---
# <a name="getsqlkeywords-method-sqlserverdatabasemetadata"></a>getSQLKeywords メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースの SQL キーワードであって、SQL92 キーワードではない、すべてのキーワードのコンマ区切りの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getSQLKeywords()  
```  
  
## <a name="return-value"></a>戻り値  
 SQL キーワードを含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLKeywords メソッドは、java.sql.DatabaseMetaData インターフェイスの getSQLKeywords メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
