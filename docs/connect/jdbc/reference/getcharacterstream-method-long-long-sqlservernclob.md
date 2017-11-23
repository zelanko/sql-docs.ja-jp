---
title: "getCharacterStream (long, long) メソッド (SQLServerNClob) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee42e6ef541b8f3c8298d467b6eb72237016efb4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>getCharacterStream (long, long) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得、 **NCLOB**データとして、**リーダー**オブジェクトまたは指定した位置と長さを持つ文字のストリームとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 A**長い**を取得する部分的な値の最初の文字のオフセットを示すです。  
  
 *length*  
  
 A**長い**を取得する部分的な値の文字の長さを示すです。  
  
## <a name="return-value"></a>戻り値  
 リーダー オブジェクトを含む、 **NCLOB**データ。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、getCharacterStream メソッド java.sql.NClob インターフェイスで指定します。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド &#40;です。SQLServerNClob &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
