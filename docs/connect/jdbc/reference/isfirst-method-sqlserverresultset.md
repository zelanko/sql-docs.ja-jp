---
title: isFirst メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c27320c78db2bd04ec9747079beb4b306446bab4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796534"
---
# <a name="isfirst-method-sqlserverresultset"></a>isFirst メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルが、この [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの先頭行にあるかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、カーソルが最初の行にします。 **false**カーソルがそれ以外の場所にある場合、または結果セットに行が含まれていない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この isFirst メソッドは、java.sql.ResultSet インターフェイスの isFirst メソッドで規定されています。  
  
 このメソッドを順方向カーソルおよび動的カーソルで使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
