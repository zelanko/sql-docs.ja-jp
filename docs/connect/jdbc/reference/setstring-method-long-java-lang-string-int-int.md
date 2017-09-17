---
title: "setString メソッド (long, java.lang.String, int, int) |Microsoft ドキュメント"
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
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 362cd4df54ee5ad826d2313341cd9ba4c7253546
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-int-int"></a>setString (long, java.lang.String, int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された文字列を、渡されたオフセットと長さに基づいて CLOB の指定された位置から書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 CLOB への書き込みを開始する位置です。  
  
 *str*  
  
 CLOB に書き込む文字列です。  
  
 *オフセット*  
  
 文字の読み取りを開始する文字列内のオフセットです。  
  
 *len 関数*  
  
 書き込む文字数です。  
  
## <a name="return-value"></a>戻り値  
 書き込まれる文字数です。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setString メソッドは、setString、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
 文字データは、指定された開始位置から上書きされ、CLOB の初期データの長さを上書きできます。 開始位置に CLOB の長さ + 1 の値を指定すると、文字列が追加されます。 開始位置に CLOB の長さ + 2 以上 (または 0 以下) の値を指定すると、位置エラーがスローされます。  
  
## <a name="see-also"></a>参照  
 [setString メソッド & #40 です。SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
