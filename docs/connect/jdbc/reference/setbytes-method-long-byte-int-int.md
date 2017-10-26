---
title: "setBytes メソッド (long, バイト、int, int) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerBlob.setBytes (long.byte[], int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7def226c-b211-459e-8c1a-08592d75d4a4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5aa6587a6877143486aa5b053311694229f10a36
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setbytes-method-long-byte-int-int"></a>setBytes (long, バイト、int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された位置、オフセット、および長さで始まる BLOB に渡された byte 配列のすべてまたは一部を書き込みます書き込まれたバイト数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes,  
                    int offset,  
                    int len)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 データの書き込みを開始する BLOB 内の位置 (1 から開始) です。  
  
 *バイト数*  
  
 BLOB に書き込む byte 配列です。  
  
 *オフセット*  
  
 内のオフセット配列からのデータの読み取りを開始する場所、**バイト**配列。  
  
 *len 関数*  
  
 byte 配列から BLOB に読み込むバイト数です。  
  
## <a name="return-value"></a>戻り値  
 **Int**書き込まれたバイト数を格納します。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setBytes メソッドは、setBytes、java.sql.Blob インターフェイスのメソッドでによって指定されます。  
  
 データは、指定した位置からは上書きされ、BLOB の初期の長さをオーバーランことができます。 開始位置に BLOB の長さ + 1 の値を指定すると、バイトが追加されます。 開始位置に BLOB の長さ + 2 以上 (または 0 以下) の値を渡すと、位置のエラーがスローされます。 長さ 0 を渡す**バイト**配列がバイトが書き込まために 0 が返されます。  
  
## <a name="see-also"></a>参照  
 [setBytes メソッド & #40 です。SQLServerBlob &#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

