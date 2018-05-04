---
title: getCharacterStream (long, long) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea78140d5a0bd24a71d9ab4c846ded3e74822f18
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getcharacterstream-method-long-long"></a>getCharacterStream (long, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、 **Clob**データ リーダー オブジェクトまたは指定した位置と長さを文字のストリームとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 A**長い**を取得する部分的な値の最初の文字のオフセットを示すです。  
  
 *長さ*  
  
 A**長い**を取得する部分的な値の文字の長さを示すです。  
  
## <a name="return-value"></a>戻り値  
 リーダー オブジェクトを含む、 **Clob**データ。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.Clob インターフェイスの getCharacterStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド&#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
