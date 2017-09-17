---
title: "setString メソッド (long, java.lang.String, int, int) - NClob |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d09ee2a09d313a192d30dc09ff07f4f3bd35d499
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString (long, java.lang.String, int, int) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたオフセットと長さに基づいて、指定した位置から始まる NCLOB に指定した文字列を書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 書き込みを開始する位置の**NCLOB**; 最初の位置は 1 です。  
  
 *str*  
  
 書き込まれる文字列、 **NCLOB**です。  
  
 *オフセット*  
  
 オフセット*str*書き込まれる文字の読み取りを開始します。  
  
 *len 関数*  
  
 書き込む文字数です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setString メソッドは、setString、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
