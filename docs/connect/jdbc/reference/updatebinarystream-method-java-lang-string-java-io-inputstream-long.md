---
title: "updateBinaryStream メソッド (java.io.InputStream, long) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3c0fb5d-ca05-43f7-9f38-fba6cf3705c6
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d8b04b7e0d45c9cfe0cb52191f0c8f6285eca22c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream-long"></a>updateBinaryStream (java.lang.String, java.io.InputStream, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列をバイナリ ストリーム値で更新します。バイナリ ストリーム値は、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 AStringthat には、列のラベルが含まれています。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 A**長い**ストリームの長さを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBinaryStream メソッドは、java.sql.ResultSet インターフェイスの updateBinaryStream メソッドによって指定されます。  
  
 このメソッドは、選択された状態に InputStream オブジェクトからバイトを渡します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、varbinary、varbinary (max)、image、xml、および udt などのバイナリ列です。 このメソッドでは、文字型の列の更新はサポートされていません。 更新するには文字型列、InputStream を使用して、 [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)メソッドです。  
  
 ストリームの長さが指定されたものと異なるかどうか、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[updateBinaryStream メソッド &#40;java.lang.String、java.io.InputStream &#41;](../../../connect/jdbc/reference/updatebinarystream-method-java-lang-string-java-io-inputstream.md)アプリケーションが列の長さがストリームを更新するときに不明なです。  
  
## <a name="see-also"></a>参照  
 [updateBinaryStream メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
