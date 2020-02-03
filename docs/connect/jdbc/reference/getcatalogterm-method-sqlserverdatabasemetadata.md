---
title: getCatalogTerm メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0aa5d372-16aa-4790-a8f6-f8b742798f8f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c0c718524b8800df02625e6392de1f9d4600291
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67953323"
---
# <a name="getcatalogterm-method-sqlserverdatabasemetadata"></a>getCatalogTerm メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース ベンダーが "カタログ" の代わりに使用している用語を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getCatalogTerm()  
```  
  
## <a name="return-value"></a>戻り値  
 カタログの用語を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCatalogTerm メソッドは、java.sql.DatabaseMetaData インターフェイスの getCatalogTerm メソッドで規定されています。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースと共に使用している場合、このメソッドでは用語 "データベース" が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
