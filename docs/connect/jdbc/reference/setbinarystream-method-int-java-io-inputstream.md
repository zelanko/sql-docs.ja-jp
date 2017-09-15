---
title: "setBinaryStream (int, java.io.InputStream) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c32b904-c44b-472e-a084-38f008a742b4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3011937144ea46a42bb0b77261c7d3261df91e70
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setbinarystream-method-int-javaioinputstream"></a>setBinaryStream (int, java.io.InputStream) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された入力ストリームに設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 Java.io.InputStream オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setBinaryStream メソッドは、java.sql.PreparedStatement インターフェイスの setBinaryStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setBinaryStream メソッド & #40 です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
