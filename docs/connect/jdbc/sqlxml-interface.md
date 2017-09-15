---
title: "SQLXML インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c636345439175c516b647a2951ac3bfa8824b06
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlxml-interface"></a>SQLXML インターフェイス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この JDBC ドライバーがサポートする JDBC 4.0 API には、java.sql.SQLXML インターフェイスが導入されています。 SQLXML インターフェイスは、対話し、XML データを操作するメソッドを定義します。 **SQLXML**データ型にマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml**データ型。  
  
 SQLXML インターフェイスと XML 値にアクセスするためのメソッドを提供、**文字列**、**リーダー**または**ライター**、または、**ストリーム**です。 を介して XML 値をアクセスすることも、**ソース**かとして設定され、**結果**、ために使用されるドキュメント オブジェクト モデル (DOM)、Simple API などの XML パーサー Api を使用した XML (SAX) および Streaming API for XML (StAX) としてXSLT で変換と XPath です。  
  
## <a name="remarks"></a>解説  
 次の表で、SQLXML インターフェイスに定義されている各メソッドについて説明します。  
  
|メソッドの構文|メソッドの説明|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|このメソッドは、SQLXML オブジェクトと、それが占有していたリソースを解放します。|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|SQLXML からデータを読み取る入力ストリームを返します。|  
|[リーダー getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|返します、 **XML** java.io.Reader オブジェクトまたは文字のストリームとしてデータ。|  
|[T 拡張ソース T getSource (クラス\<T > sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|返します、**ソース**を読み取り、 **XML**こので指定された値**SQLXML**オブジェクト。<br /><br /> **注:** getSource メソッドは、次のソースをサポートしています。 は、javax.xml.transform.sax.SAXSource、javax.xml.transform.stax.StAXSource、java.io.InputStream です。|  
|[文字列の保存](http://go.microsoft.com/fwlink/?LinkId=131757)|文字列表現を返します、 **XML**この SQLXML オブジェクトによって指定された値。|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|書き込みに使用できるストリームを取得、 **XML**この SQLXML オブジェクトを表す値です。|  
|[ライター setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|書き込みに使用するストリームを返す、 **XML**この SQLXML オブジェクトを表す値です。|  
|[T 拡張結果 T setResult (クラス\<T > resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|返します、**結果**設定、 **XML**こので指定された値**SQLXML**オブジェクト。<br /><br /> **注:** setResult メソッドは、次のソースをサポートしています。 は、javax.xml.transform.sax.SAXResult、javax.xml.transform.stax.StaxResult、およびします。|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|この SQLXML オブジェクトを指定したによって指定された XML 値を設定**文字列**表現します。|  
  
 アプリケーションから SQLXML オブジェクトを介して XML 値の読み取りと書き込みを行うことができるのは 1 回だけです。  
  
 Free() メソッドが呼び出されると、SQLXML オブジェクトは無効なようになり、読み取りも書き込みもです。 アプリケーションが free() メソッド以外には、その SQLXML オブジェクトに対してメソッドを呼び出すしようとすると、例外がスローされます。  
  
 アプリケーションは、次の get アクセス操作子メソッドのいずれかを呼び出したときに、SQLXML オブジェクトは読み取りも書き込みも: getSource、getCharacterStream、getBinaryStream、getString とします。  
  
 アプリケーションでは、次のいずれかの set アクセス操作子を呼び出すとき、SQLXML オブジェクトはどちらも書き込みも読み取り: setResult、setCharacterStream、setBinaryStream、setString とします。  
  
## <a name="see-also"></a>参照  
 [XML データのサポート](../../connect/jdbc/supporting-xml-data.md)  
  
  
