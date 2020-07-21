---
title: getFetchSize メソッド (SQLServerResultSet) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf50f1eacc88d6aa2786bcda1f740c673c55a859
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924818"
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
  
## <a name="remarks"></a>解説  
 この getFetchSize メソッドは、java.sql.ResultSet インターフェイスの getFetchSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
