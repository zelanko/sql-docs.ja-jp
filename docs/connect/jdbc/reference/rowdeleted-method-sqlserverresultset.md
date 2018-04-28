---
title: rowDeleted メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
apiname:
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 96a38e82a5a5d7435f1b5ee256189855d6ab7a7c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行が削除されたかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**行は削除され、削除が検出された場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この rowDeleted メソッドは、java.sql.ResultSet インターフェイスの rowDeleted メソッドによって指定されます。  
  
 削除された行は、結果セット内に可視の穴を残すことがあります。 このメソッドは、結果セット内の穴を検出するために使用できます。 返される値は異なるかどうかこの[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが削除を検出できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 検出は順方向カーソルと動的カーソルの一時的なものが、すべての更新可能なカーソルの種類の削除された行を検出します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
