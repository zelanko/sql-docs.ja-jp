---
title: getBytes メソッド (SQLServerBlob) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c595ab80b1fa40b3c971af5e5152c7186f4d59d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getbytes-method-sqlserverblob"></a>getBytes メソッド (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  BLOB データを byte 配列として取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 開始位置です。1 から始まります (0 ではありません)。  
  
 *長さ*  
  
 取得するデータの長さです。  
  
## <a name="return-value"></a>戻り値  
 A**バイト**要求されたデータを含む配列。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBytes メソッドは、java.sql.Blob インターフェイスの getBytes メソッドによって指定されます。  
  
 Null または長さ 0 の BLOB があるし、位置 1 の場合、空で正確に 0 バイトを取得しようとしています。 場合**バイト**配列が返されます (長さが 0 の byte 配列)。  
  
 null または長さが 0 の BLOB があり、位置 1 以外の場所で任意の長さのバイトを取得しようとすると、位置の例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
