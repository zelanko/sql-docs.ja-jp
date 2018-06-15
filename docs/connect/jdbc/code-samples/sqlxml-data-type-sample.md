---
title: SQLXML データ型のサンプル |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35259e7c9f6bc0129933117b0202b4ec61e52010
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833757"
---
# <a name="sqlxml-data-type-sample"></a>SQLXML データ型のサンプル
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サンプル アプリケーションは、リレーショナル データベースに XML データを格納する方法、データベースから XML データを取得する方法、およびと XML データを解析する方法を示しています、 **SQLXML** Java データ型。  
  
 このセクションのコード例には、Simple API for XML (SAX) パーサーが使用されます。 SAX はイベント ベースで XML ドキュメントを解析する用途向けに、有志で策定された標準です。 XML データを操作するためのアプリケーション プログラミング インターフェイスも用意されています。 このアプリケーションでは、Document Object Model (DOM)、Streaming API for XML (StAX) など、他の任意の XML パーサーも利用できます。  
  
 Document Object Model (DOM) は、XML のドキュメント、フラグメント、ノード、またはノード セットのプログラミング的な表現を可能にします。 XML データを操作するためのアプリケーション プログラミング インターフェイスも用意されています。 同様に、Streaming API for XML (StAX) は、XML のプル解析を可能にする Java ベースの API です。  
  
> [!IMPORTANT]  
>  SAX パーサー API を使用するには、javax.xml パッケージから、標準の SAX 実装をインポートする必要があります。  
  
 このサンプルのコード ファイルは sqlxmlExample.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\datatypes  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するには、クラスパスを設定して sqljdbc4.jar ファイルを含める必要があります。 クラスパスに sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という例外がスローされます。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
 さらへのアクセスが必要な[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]このサンプル アプリケーションを実行するサンプル データベース。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードへの接続、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]データベースして createSampleTables メソッドを呼び出します。  
  
 createSampleTables メソッドは、テスト テーブル (TestTable1 および TestTable2) が存在する場合、これらのテーブルを削除します。 そのうえで、TestTable1 に 2 つの行を挿入します。  
  
 また、コード サンプルには、後述する 3 つのメソッドと 1 つのクラス (ExampleContentHandler) が含まれています。  
  
 ExampleContentHandler クラスには、パーサー イベント用のメソッドを定義したカスタム コンテンツ ハンドラーが実装されています。  
  
 showGetters メソッドは、SQLXML オブジェクト内のデータを、SAX、ContentHandler、および XMLReader を使用して解析します。 まず、カスタム コンテンツ ハンドラー (ExampleContentHandler) のインスタンスを作成します。 次に、TestTable1 から一連のデータを返す SQL ステートメントを作成して実行します。 さらに、SAX パーサーを取得して、XML データを解析します。  
  
 ShowSetters メソッドを設定する方法、 **xml** SAX、ContentHandler、および ResultSet を使用して列です。 最初を使用して空の SQLXML オブジェクトを作成、 [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) Connection クラスのメソッドです。 次に、コンテンツ ハンドラーのインスタンスを取得して、そのデータを SQLXML オブジェクトに書き込みます。 その後、データを TestTable1 に書き込みます。 最後に、サンプル コードは、結果セットに含まれているデータの行を反復処理しを使用して、 [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) XML データを読み取ります。  
  
 showTransformer メソッドは、一方のテーブルから XML データを取得し、SAX および Transformer を使用して、その XML データを別のテーブルに挿入します。 最初に、TestTable1 からソース SQLXML オブジェクトを取得します。 使用して空の送信先 SQLXML オブジェクトを作成し、 [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) Connection クラスのメソッドです。 その後、ターゲットの SQLXML オブジェクトを更新し、XML データを TestTable2 に書き込みます。 最後に、サンプル コードは、結果セットに含まれているデータの行を反復処理しを使用して、 [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) TestTable2 の XML データを読み取ります。  
  
 [!code[JDBC#UsingSQLXML1](../../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]  
  
## <a name="see-also"></a>参照  
 [データ型の処理 &#40;JDBC&#41;](../../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
