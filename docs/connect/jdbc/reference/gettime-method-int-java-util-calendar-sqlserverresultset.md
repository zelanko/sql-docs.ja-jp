---
title: "getTime (int, java.util.Calendar) メソッド (SQLServerResultSet) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.getTime (int, java.util.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d21e0c1d-9d6e-468f-8b11-cc7209b2c2e5
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acc163a76be61a998feed61ede84afcf5edd920e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="gettime-method-int-javautilcalendar-sqlserverresultset"></a>getTime (int, java.util.Calendar) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語を渡された Calendar オブジェクトを使用しての java.sql.Time オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Time getTime(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
 *cal*  
  
 予定表オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 Time オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTime メソッドは、java.sql.ResultSet インターフェイスの getTime メソッドによって指定されます。  
  
 このメソッドの有効な時刻部分を返します、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] datetime または smalldatetime データ型の日付部分の 1970/01/01 から、指定されたカレンダーのタイムゾーンにおける Java のベースラインの日付に設定します。  
  
## <a name="see-also"></a>参照  
 [getTime メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
