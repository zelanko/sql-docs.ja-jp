---
title: "updateTime (int, java.sql.Time) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.updateTime (int, java.sql.Time)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fa7a3ca5-1111-4480-97ca-65b632aa1e5b
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 345d7146ffec61068f97aa3581b39c6b9434f32f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updatetime-method-int-javasqltime"></a>updateTime (int, java.sql.Time) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスを使用して、指定された列を時刻の値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateTime(int index,  
                       java.sql.Time x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**列インデックスを示すです。  
  
 *x*  
  
 時刻値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateTime メソッドは、java.sql.ResultSet インターフェイスの updateTime メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateTime メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
