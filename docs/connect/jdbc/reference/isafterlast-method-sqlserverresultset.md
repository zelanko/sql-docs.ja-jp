---
title: isAfterLast メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isAfterLast
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19f9d124-3184-4985-8b97-503a8ab8b4f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 874677b8e82ef9129615daed2170757e908f9455
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809870"
---
# <a name="isafterlast-method-sqlserverresultset"></a>isAfterLast メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルが、[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの最終行の後ろにあるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isAfterLast()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**カーソルが最終行の後ろにある場合。 **false**カーソルがそれ以外の場所にある場合、または結果セットに行が含まれていない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この isAfterLast メソッドは、java.sql.ResultSet インターフェイスの isAfterLast メソッドによって指定されます。  
  
 このメソッドが動的カーソル (順方向専用、読み取り専用カーソルを含む) で使用され、selectMethod 接続プロパティが "cursor" に設定されている場合は、例外が発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
