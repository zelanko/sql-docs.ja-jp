---
title: getArray (int) メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getArray (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 377746c7-8c9c-41f5-8490-ca0dd56fd57a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f5fc905d2b92235e0ea0b1093e1b76a374a5aeb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getarray-method-int-sqlserverresultset"></a>getArray (int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトの配列オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Array getArray(int i)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *私*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 配列オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getArray メソッドは、java.sql.ResultSet インターフェイスの getArray メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getArray メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
