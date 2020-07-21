---
title: jdbcCompliant メソッド (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ae5ac88d0427a605493bc19786bdd5f23dc93b6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915066"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>jdbcCompliant メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] が JDBC 仕様に準拠しているかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>戻り値  
 JDBC ドライバーが最低限の要件を満たしている場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 この jdbcCompliant メソッドは、java.sql.Driver インターフェイスの jdbcCompliant メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
