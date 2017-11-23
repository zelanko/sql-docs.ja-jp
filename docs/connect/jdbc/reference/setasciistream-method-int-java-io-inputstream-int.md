---
title: "setAsciiStream (int、java.io.InputStream, int) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerPreparedStatement.setAsciiStream
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9436c39f-f1a1-484a-a75b-776a72ca70f4
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 420ff08a23435b74150bd4503a13745508585618
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setasciistream-method-int-javaioinputstream-int"></a>setAsciiStream (int, java.io.InputStream, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたバイト数で指定された InputStream オブジェクトに指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setAsciiStream(int n,  
                                 java.io.InputStream x,  
                                 int length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 バイト数です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setAsciiStream メソッドは、java.sql.PreparedStatement インターフェイスの setAsciiStream メソッドによって指定されます。  
  
 ストリームの長さがで指定されているとは異なる場合、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[setAsciiStream メソッド (&) #40 です。 int, java.io.InputStream &#41;](../../../connect/jdbc/reference/setasciistream-method-int-java-io-inputstream.md)アプリケーションが列の長さが不明なストリームを更新するときにします。  
  
## <a name="see-also"></a>参照  
 [setAsciiStream メソッド &#40;です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
