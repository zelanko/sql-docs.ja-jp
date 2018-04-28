---
title: getRef (int) メソッド |Microsoft ドキュメント
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
- SQLServerCallableStatement.getRef (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 905dd02a-0c7f-475b-8be4-341b4359c766
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 637a8b540f44b960d3c2c59fb0d1bc4da67c484c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getref-method-int"></a>getRef (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Java プログラミング言語のパラメーターのインデックスの Ref オブジェクトとして指定されたパラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Ref getRef(int i)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *私*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 Ref オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getRef メソッドは、java.sql.CallableStatement インターフェイスの getRef メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getRef メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
