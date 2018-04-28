---
title: getURL (java.lang.String) メソッド |Microsoft ドキュメント
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
- SQLServerCallableStatement.getURL (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb709f6b-64e1-4d0c-a704-290891627dd7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: adf8d1a5f7bb3d07c1b6722444c817f21c3c4161
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="geturl-method-javalangstring"></a>getURL (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーター名を指定、Java プログラミング言語で URL オブジェクトとして指定されたパラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.net.URL getURL(java.lang.String s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *S*  
  
 A**文字列**パラメーター名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 URL のオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getURL メソッドは、java.sql.CallableStatement インターフェイスの getURL メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getURL メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
