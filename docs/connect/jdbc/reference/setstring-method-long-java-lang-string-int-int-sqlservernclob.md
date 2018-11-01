---
title: setString メソッド (long, java.lang.String, int, int) - NClob |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58a26b71787e154acec6add71ecc868b438c2dec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810730"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString (long, java.lang.String, int, int) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された文字列を、指定されたオフセットと長さに基づいて NCLOB の指定された位置から書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 **NCLOB** 値への書き込みを開始する位置です。最初の位置は 1 です。  
  
 *str*  
  
 **NCLOB** に書き込む文字列です。  
  
 *offset*  
  
 書き込む文字の読み取りを開始する *str* へのオフセットです。  
  
 *len*  
  
 書き込む文字数です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setString メソッドは、java.sql.NClob インターフェイスで、setString メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
