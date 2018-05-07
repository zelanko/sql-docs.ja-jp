---
title: setString (long, java.lang.String) - メソッド NClob |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc953a2026bf4fca9401b1eb9484ff9f34435e2e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>setString (long, java.lang.String) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  書き込み、指定した**文字列**を**NCLOB**開始位置から指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 書き込みを開始する位置の**NCLOB**; 最初の位置は 1 です。  
  
 *str*  
  
 書き込まれる文字列、 **NCLOB**です。  
  
## <a name="return-value"></a>戻り値  
 書き込まれる文字数です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setString メソッドは、setString、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
