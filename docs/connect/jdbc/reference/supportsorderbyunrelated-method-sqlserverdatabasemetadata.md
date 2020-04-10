---
title: supportsOrderByUnrelated メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOrderByUnrelated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9ea6c534-8132-49f3-aac3-a12ec4c46df2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33526c2b101fb26d8668b13d7d467e3cf7c699bd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923051"
---
# <a name="supportsorderbyunrelated-method-sqlserverdatabasemetadata"></a>supportsOrderByUnrelated メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが、ORDER BY 句で SELECT ステートメントにない列の使用をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsOrderByUnrelated()  
```  
  
## <a name="return-value"></a>戻り値  
 サポートされている場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsOrderByUnrelated メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsOrderByUnrelated メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
