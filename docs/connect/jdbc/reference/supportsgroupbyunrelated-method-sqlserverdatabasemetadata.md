---
title: supportsGroupByUnrelated メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsGroupByUnrelated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 455fe02e-3877-409b-8281-8e0491acd3e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 752cb296b58c0528ad419e8507ea304eca6bd340
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924692"
---
# <a name="supportsgroupbyunrelated-method-sqlserverdatabasemetadata"></a>supportsGroupByUnrelated メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが GROUP BY 句で SELECT ステートメントにない列の使用をサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsGroupByUnrelated()  
```  
  
## <a name="return-value"></a>戻り値  
 サポートされている場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsGroupByUnrelated メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsGroupByUnrelated メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
