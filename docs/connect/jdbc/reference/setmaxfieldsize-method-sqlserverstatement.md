---
title: setMaxFieldSize メソッド (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.setMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e44e19c42a9ac0ec5629362dff4d33116c64090
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842787"
---
# <a name="setmaxfieldsize-method-sqlserverstatement"></a>setMaxFieldSize メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  内のバイトの最大数の上限を設定、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)文字またはバイナリ値を指定したバイト数を格納する列。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *max*  
  
 **Int**バイトの最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setMaxFieldSize メソッドは、java.sql.Statement インターフェイスの setMaxFieldSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
