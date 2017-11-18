---
title: "setLockTimeout メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4d3801e4494ae42cabc1d3ca149669a66273574
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>setLockTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *lockTimeout*  
  
 **Int**待機するミリ秒数を含む値です。  
  
## <a name="remarks"></a>解説  
 ロック タイムアウトは、データベースがロック タイムアウトを通知するまでに待機する時間 (ミリ秒) です。既定値の -1 は、無制限に待機することを意味します。 値を指定した場合、接続上のすべてのステートメントに対する既定値になります。  
  
> [!NOTE]  
>  値 0 を指定した場合、待機が行われません。 LockTimeout プロパティが設定されていない場合、 [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)メソッドは、既定値は-1 を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

