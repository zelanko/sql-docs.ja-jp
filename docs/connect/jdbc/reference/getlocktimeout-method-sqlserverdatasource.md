---
title: "getLockTimeout メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: edbd984352f2b75711e9fc9a445a84066fb9f0ac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>getLockTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**データベースが待機するミリ秒数を含む値です。  
  
## <a name="remarks"></a>解説  
 ロック タイムアウトは、データベースがロック タイムアウトを通知するまでに待機する時間 (ミリ秒) です。既定値の -1 は、無制限に待機することを意味します。 値を指定した場合、接続上のすべてのステートメントに対する既定値になります。  
  
> [!NOTE]  
>  値 0 を指定した場合、待機が行われません。 lockTimeout プロパティが設定されていない場合、getLockTimeout メソッドは既定値の -1 を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

