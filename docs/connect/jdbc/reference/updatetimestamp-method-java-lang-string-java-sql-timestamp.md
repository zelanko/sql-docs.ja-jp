---
title: updateTimestamp (java.lang.String, java.sql.Timestamp) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateTimestamp (java.lang.String, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d468357-bf73-484c-9a30-3671e399cf26
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bb80e0cfa79f6d93c9702c9bee953bf72b08ada3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788912"
---
# <a name="updatetimestamp-method-javalangstring-javasqltimestamp"></a>updateTimestamp (java.lang.String, java.sql.Timestamp) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列をタイムスタンプ値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateTimestamp(java.lang.String columnName,  
                            java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *x*  
  
 タイムスタンプ値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateTimestamp メソッドは、java.sql.ResultSet インターフェイスの updateTimestamp メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateTimestamp メソッド (SQLServerResultSet)](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
