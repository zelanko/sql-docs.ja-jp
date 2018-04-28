---
title: findColumn メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerResultSet.findColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c29994a-0b53-420b-8a9b-82a9eef08587
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 541bf938b386705e573d79b4017c8aa6cffb1b88
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="findcolumn-method-sqlserverresultset"></a>findColumn メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これで指定された列名の最初の一致する列のインデックスを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int findColumn(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 **Int**列インデックスを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この findColumn メソッドは、java.sql.ResultSet インターフェイスの findColumn メソッドによって指定されます。  
  
 同じ名前の複数の列がある場合、findColumn メソッドは最初、大文字と小文字を返します。 大文字と小文字を区別して一致する列が存在しない場合は、大文字と小文字の区別に関係なく最初に一致した列を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
