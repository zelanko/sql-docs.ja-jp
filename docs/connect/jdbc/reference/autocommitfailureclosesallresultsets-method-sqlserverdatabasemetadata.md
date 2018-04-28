---
title: JDBC ドライバーは、開いている結果セットを閉じる |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04362a4e36ef7acdb7fb43ad45169b203782be0a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>autoCommitFailureClosesAllResultSets メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  自動コミットが有効である場合に例外が発生したとき、保持可能な結果セットも含め、開いているすべての結果セットを JDBC ドライバーで閉じるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**開いているすべての結果など、保持可能なセットが閉じますを自動コミットが有効にし、例外が発生します。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この autoCommitFailureClosesAllResultSets メソッドは、java.sql.DatabaseMetaData インターフェイスの autoCommitFailureClosesAllResultSets メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
