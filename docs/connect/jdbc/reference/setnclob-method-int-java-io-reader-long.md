---
title: "setNClob (int, java.io.Reader, long) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62dd2f77581dc6bab9488a6967129983668f057f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setnclob-method-int-javaioreader-long"></a>setNClob (int, java.io.Reader, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された文字数は、指定したリーダー オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 **Int**パラメーター インデックスを示すです。  
  
 *リーダー*  
  
 パラメーターの値を示すリーダー オブジェクト。  
  
 *length*  
  
 **長い**パラメーター値の文字数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNClob メソッドは、java.sql.PreparedStatement インターフェイスの setNClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setNClob メソッド & #40 です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
