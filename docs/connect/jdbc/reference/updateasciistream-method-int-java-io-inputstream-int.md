---
title: updateAsciiStream メソッド (java.io.InputStream, int) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateAsciiStream (int, java.io.InputStream.int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d07944b8-7001-49b5-b3b3-0676f71e17cf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 430bda14f1c9c69a11e6b6617e34b774a9fa01c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713030"
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
 *index*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 ストリームの長さを示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateAsciiStream メソッドは、java.sql.ResultSet インターフェイスの updateAsciiStream メソッドによって指定されます。  
  
 このメソッドは、ASCII 文字 (バイト) を、InputStream オブジェクトから変換可能な文字型の列へ渡します。ASCII 文字の変換可能な文字型の列は、Unicode の 874、932、936、949、950、1250 - 1258 コード ページの ASCII の範囲 [0x00 – 0x7F] です。 このメソッドは、対象となる照合順序ページへの変換を実行します。 変換できない変換先列を更新しようとすると、例外がスローされます。 バイナリ列の場合、そのままのバイトが渡されます。  
  
 ストリームの長さが、*length* パラメーターで指定された長さと異なる場合は、行の更新または挿入時に JDBC ドライバーが例外をスローします。  
  
 ストリームの長さが不明である場合、*length* パラメーターを -1 に設定して、ドライバーが長さに関係なくストリームを受け入れるように指定できます。 sqljdbc4.jar を使用する場合、アプリケーションで長さが不明なストリームを使用して列を更新するときには、JDBC 4.0 メソッドの [updateAsciiStream &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/updateasciistream-method-int-java-io-inputstream.md) メソッドを使用することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [updateAsciiStream メソッド (SQLServerResultSet)](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
