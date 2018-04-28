---
title: getTimestamp (int) メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.getTimestamp (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ad538a76-983f-4175-9481-9e7fa9480c71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 085e84d05b082154718670a5d956dc27e2fe7e34
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettimestamp-method-int-sqlserverresultset"></a>getTimestamp (int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語の java.sql.Timestamp オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 タイムスタンプ オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTimestamp メソッドは、java.sql.ResultSet インターフェイスの getTimestamp メソッドによって指定されます。  
  
 このメソッドからのみ値を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]datetime および smalldatetime の列です。  
  
## <a name="see-also"></a>参照  
 [getTimestamp メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
