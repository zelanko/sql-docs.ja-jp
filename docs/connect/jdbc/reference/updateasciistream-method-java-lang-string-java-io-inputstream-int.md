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
- SQLServerResultSet.updateAsciiStream (java.lang.String, java.io.InputStream, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4e2997a0-c18e-4114-bce9-0ab4b2b9f92c
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f9282ddb3be8df13bf40875458264913044f3c6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updateasciistream-method-javalangstring-javaioinputstream-int"></a>updateAsciiStream (java.lang.String, java.io.InputStream, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列名を ASCII ストリーム値で更新します。ASCII ストリーム値は、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateAsciiStream(java.lang.String columnName,  
                              java.io.InputStream x,  
                              int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 **Int**ストリームの長さを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateAsciiStream メソッドは、java.sql.ResultSet インターフェイスの updateAsciiStream メソッドによって指定されます。  
  
 このメソッドでは、InputStream オブジェクトから ASCII 文字 (バイト単位) を渡しますに変換できる文字列は、ASCII の範囲 [0x00 – 0x7F] Unicode、および 874、932、936、949、950、1250 ~ 1258 コード ページのです。 このメソッドは、対象となる照合順序ページへの変換を実行します。 変換できない変換先列を更新しようとすると、例外がスローされます。 バイナリ列の場合、そのままのバイトが渡されます。  
  
 ストリームの長さがで指定されているとは異なる場合、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[updateAsciiStream メソッド &#40;java.lang.String、java.io.InputStream &#41;](../../../connect/jdbc/reference/updateasciistream-method-java-lang-string-java-io-inputstream.md)アプリケーションが列の長さがストリームを更新するときに不明なです。  
  
## <a name="see-also"></a>参照  
 [updateAsciiStream メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
