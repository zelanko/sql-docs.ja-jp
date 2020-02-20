---
title: moveToCurrentRow メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11a92c879995d198658853ef9b5cec9d00449230
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67976829"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>moveToCurrentRow メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  記憶されているカーソル位置 (通常は現在の行) に、カーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この moveToCurrentRow メソッドは、java.sql.ResultSet インターフェイスの moveToCurrentRow メソッドによって指定されます。  
  
 このメソッドは、カーソルが挿入行にない場合は無効です。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
