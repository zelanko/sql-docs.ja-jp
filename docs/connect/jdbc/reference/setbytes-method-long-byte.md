---
title: setBytes メソッド (long, バイト) |Microsoft ドキュメント
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
- SQLServerBlob.setBytes (long.byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffb8f107-0f9d-4410-957f-62b718e1e872
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f164a93981bb45d5d3cb5fdba973de4790ca7db5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841507"
---
# <a name="setbytes-method-long-byte"></a>setBytes メソッド (long, バイト)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された byte 配列を、渡された位置から BLOB に書き込み、書き込んだバイト数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 (1 から始まる) のデータの書き込みを開始する BLOB 内の位置。  
  
 *バイト数*  
  
 BLOB に書き込む byte 配列です。  
  
## <a name="return-value"></a>戻り値  
 A**長い**書き込まれたバイト数を指定する値。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setBytes メソッドは、setBytes、java.sql.Blob インターフェイスのメソッドでによって指定されます。  
  
 データは指定された開始位置から上書きされ、BLOB の初期データの長さをオーバーランすることができます。 開始位置に BLOB の長さ + 1 の値を指定すると、バイトが追加されます。 開始位置に BLOB の長さ + 2 以上 (または 0 以下) の値を渡すと、位置のエラーがスローされます。 長さ 0 を渡す**バイト**配列がバイトが書き込まために 0 が返されます。  
  
## <a name="see-also"></a>参照  
 [setBytes メソッド&#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
