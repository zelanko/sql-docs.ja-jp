---
title: absolute メソッド (SQLServerResultSet) |Microsoft ドキュメント
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
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00f6188a1dbaaff06d2cb3f6ccb0c3ffef8d93bd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="absolute-method-sqlserverresultset"></a>absolute メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この特定の行にカーソルを移動[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *行*  
  
 **Int**に移動する行番号を示すです。 正の値、負の値、または 0 を指定できます。  
  
## <a name="return-value"></a>戻り値  
 **true**の指定された位置にカーソルが移動された場合。 **false**最初の行の前に、または最終行の後である場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この絶対メソッドは、java.sql.ResultSet インターフェイスの絶対メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
