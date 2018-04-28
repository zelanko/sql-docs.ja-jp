---
title: rowInserted メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 661268b75a5500ebf494965f1bf94fe7de2fafcd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の行に挿入があったかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**行が挿入があったし、挿入が検出された場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この rowUpdated メソッドは、java.sql.ResultSet インターフェイスの rowUpdated メソッドによって指定されます。  
  
 返される値は異なるかどうかこの[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトが表示される挿入を検出できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] どの種類のカーソルの挿入された行は検出されません。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
