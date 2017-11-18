---
title: "setUser メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bdb6e334866ae6561fc770c36dfcfa4c0f0a4898
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setuser-method-sqlserverdatasource"></a>setUser メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるユーザー名を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ユーザー*  
  
 A**文字列**ユーザー名を格納しています。  
  
## <a name="remarks"></a>解説  
 SetUser メソッドへの接続に使用されるユーザー名を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 ユーザー名の値が設定されていない場合、 [getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)メソッドは、既定値は null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

