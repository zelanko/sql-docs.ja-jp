---
title: "updateDateTimeOffset(string) (SQLServerResultSet) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 952947ce-7c6e-4364-b035-46cb7fe621b2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee7ddcee503aff8481b5c996fcb59f7e1ac50e2a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatedatetimeoffsetstring-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(string, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドで追加された[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 です。  
  
 指定された列の値を更新、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値、列名を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列の名前。  
  
 *x*  
  
 A [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 取得することができます、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値と[SQLServerResultSet.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)です。  
  
## <a name="see-also"></a>参照  
 [updateDateTimeOffset & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

