---
title: deleteRow メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd06dec2dccd3e124d702131aa4520a394ecd9fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これから現在の行を削除[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトと基になるデータベースからです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この deleteRow メソッドは、java.sql.ResultSet インターフェイスの deleteRow メソッドによって指定されます。  
  
 カーソルが挿入行にあるときは、このメソッドを呼び出すことができません。  
  
 キーセット カーソルが使用されると、このメソッドは結果セットに穴を残します。 使用してこの穴をテストすることができます、 [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)メソッドです。 結果セット内の行の行番号は変更されません。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
