---
title: "updateClob (int, java.sql.Clob) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.updateClob (int, java.sql.Clob)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d2a5e9cb-2631-4f6e-a90c-4bee58e2f7b8
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b890ac1d5ff15ba51a39638fc26e55c74d3fe957
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updateclob-method-int-javasqlclob"></a>updateClob (int, java.sql.Clob) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスを使用して、指定された列を java.sql.Clob 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateClob(int columnIndex,  
                       java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
 *clobValue*  
  
 Clob オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateClob メソッドは、java.sql.ResultSet インターフェイスの updateClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateClob メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
