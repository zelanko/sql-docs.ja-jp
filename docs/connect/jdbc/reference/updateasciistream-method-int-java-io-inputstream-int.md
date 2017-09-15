---
title: "updateAsciiStream メソッド (java.io.InputStream, int) |Microsoft ドキュメント"
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
- SQLServerResultSet.updateAsciiStream (int, java.io.InputStream.int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d07944b8-7001-49b5-b3b3-0676f71e17cf
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e60544cf133d302d4b2ec329b7bc648d543035f2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updateasciistream-method-int-javaioinputstream-int"></a>updateAsciiStream (int, java.io.InputStream, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列を ASCII ストリーム値で更新します。ASCII ストリーム値は、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateAsciiStream(int index,  
                              java.io.InputStream x,  
                              int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**列インデックスを示すです。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 **Int**ストリームの長さを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateAsciiStream メソッドは、java.sql.ResultSet インターフェイスの updateAsciiStream メソッドによって指定されます。  
  
 このメソッドでは、InputStream オブジェクトから ASCII 文字 (バイト単位) を渡しますに変換できる文字列は、ASCII の範囲 [0x00 – 0x7F] Unicode、および 874、932、936、949、950、1250 ~ 1258 コード ページのです。 このメソッドは、対象となる照合順序ページへの変換を実行します。 変換できない変換先列を更新しようとすると、例外がスローされます。 バイナリ列の場合、そのままのバイトが渡されます。  
  
 ストリームの長さが指定されたものと異なるかどうか、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[updateAsciiStream メソッド (&) #40 です。 int, java.io.InputStream &#41;](../../../connect/jdbc/reference/updateasciistream-method-int-java-io-inputstream.md)アプリケーションが列の長さが不明なストリームを更新するときにします。  
  
## <a name="see-also"></a>参照  
 [updateAsciiStream メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
