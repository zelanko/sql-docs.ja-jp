---
title: truncate メソッド (SQLServerClob) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerClob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea3b2a03-387e-49d7-a4d6-ca6a6a354c90
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d178998138973332521a44437af47263e6289f7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="truncate-method-sqlserverclob"></a>truncate メソッド (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  CLOB を指定された長さに切り捨てます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *len*  
  
 CLOB を切り捨てた後に残す長さ (文字数) です。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この切り捨てメソッドは、切り捨て、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
