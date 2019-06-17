---
title: getFetchSize メソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7bc96930-b0c9-42f6-8df9-1d8d824408b3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b96c3112e2e207edc7cf9bbe3ae80eb5393eb9b2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802032"
---
# <a name="getfetchsize-method-sqlserverresultset"></a>getFetchSize メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトのフェッチ サイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getFetchSize()  
```  
  
## <a name="return-value"></a>戻り値  
 現在のフェッチ サイズを示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getFetchSize メソッドは、java.sql.ResultSet インターフェイスの getFetchSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
