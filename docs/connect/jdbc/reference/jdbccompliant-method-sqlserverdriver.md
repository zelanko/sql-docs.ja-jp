---
title: jdbcCompliant メソッド (SQLServerDriver) |Microsoft ドキュメント
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
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 357024153bb862ff369278096018dd544ead4ca8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840347"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>jdbcCompliant メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  あることを確認、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は JDBC 仕様に準拠していません。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>戻り値  
 **true** JDBC ドライバーが最小要件を満たす場合です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 この jdbcCompliant メソッドは、java.sql.Driver インターフェイスの jdbcCompliant メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
