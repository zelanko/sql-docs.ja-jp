---
title: rowDeleted メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b99e2f6f7bc289e123c36e3a528ec937e0f5f7ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605610"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行が削除されたかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>戻り値  
 行が削除されていることが検出された場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この rowDeleted メソッドは、java.sql.ResultSet インターフェイスの rowDeleted メソッドによって指定されます。  
  
 削除された行は、結果セット内に可視の穴を残すことがあります。 このメソッドは、結果セット内の穴を検出するために使用できます。 返される値は、この [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトが削除を検出できるかどうかによって異なります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、更新可能なすべての種類のカーソルについて、削除された行が検出されます。ただし、順方向カーソルおよび動的カーソルの場合、検出は一時的です。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
