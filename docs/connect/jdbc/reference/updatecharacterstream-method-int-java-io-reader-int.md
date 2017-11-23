---
title: "updateCharacterStream メソッド (java.io.Reader, int) |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.updateCharacterStream (int, java.io.Reader, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b692c372-f6d7-4528-9c5d-cd8421bdb12e
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 905ba5f6eda47ceacb9b86f62f8baf5a47a0929b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updatecharacterstream-method-int-javaioreader-int"></a>updateCharacterStream (int, java.io.Reader, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列を文字ストリームの値で更新します。文字ストリームの値は、指定された文字数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateCharacterStream(int columnIndex,  
                                  java.io.Reader readerValue,  
                                  int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
 *readerValue*  
  
 リーダー オブジェクト。  
  
 *length*  
  
 **Int**ストリームの長さを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateCharacterStream メソッドは、java.sql.ResultSet インターフェイスの updateCharacterStream メソッドによって指定されます。  
  
 このメソッドは、選択したテキストとバイナリ列に、リーダー オブジェクトから Unicode 文字を渡します。 これには、すべてのテキスト列が含まれますと**バイナリ**、 **varbinary**、 **varbinary (max)**、**イメージ**、および**xml**列がない**udt**列です。  
  
 ストリームの長さがで指定されているとは異なる場合、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[updateCharacterStream メソッド (&) #40 です。 int, java.io.Reader &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-int-java-io-reader.md)アプリケーションが列の長さが不明なストリームを更新するときにします。  
  
## <a name="see-also"></a>参照  
 [updateCharacterStream メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
