---
title: "getFailoverPartner メソッド (SQLServerDataSource) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f2b5076573d1513313949a5ad9b558a24315bf5c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>getFailoverPartner メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**が設定されていない場合、フェールオーバー パートナーの名前を含むです。  
  
## <a name="remarks"></a>解説  
 フェールオーバー パートナー名セットを使用して、このメソッドによって返される値の反映、 [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

