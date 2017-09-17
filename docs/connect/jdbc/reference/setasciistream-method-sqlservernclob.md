---
title: "setAsciiStream メソッド (SQLServerNClob) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e66738bf3941038ae94aa6bc03464a9c28ade457
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setasciistream-method-sqlservernclob"></a>setAsciiStream メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ASCII の書き込みに使用するストリームが文字を取得、 **NCLOB**値**java.sql.NClob**オブジェクトが表す、指定された位置を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 書き込みを開始する位置の**NCLOB**オブジェクトです。 最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 OutputStream を表すオブジェクトを ASCII エンコードされた文字のストリームを書き込むことができます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setAsciiStream メソッドは、setAsciiStream、java.sql.NClob インターフェイスのメソッドでによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
