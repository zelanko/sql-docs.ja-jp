---
title: SqlXmlCommand オブジェクト (SQLXML マネージ クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a5e468796d1acaf2c5b5cc0fbefe8502aa04732a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32973587"
---
# <a name="sqlxml-managed-classes---sqlxmlcommand-object"></a>SQLXML マネージ クラス - SqlXmlCommand オブジェクト
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SqlXmlCommand オブジェクトのコンス トラクターは、次に示します。  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 ここで、`cnString` は `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` のように、サーバー、データベース、およびログイン情報を識別する ADO または OLEDB 接続文字列です。  
  
 接続文字列では、`Provider` に SQLOLEDB を指定する必要があります。プロバイダーの文字列に `Data Provider` は使用できません。  
  
 作業用サンプルについては、次を参照してください。 [SQL クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md).  
  
## <a name="methods"></a>メソッド  
 TheSqlXmlCommand オブジェクトには、以下のコマンドを実行する方法を含め、いくつかの方法がサポートされています。  
  
 void ExecuteNonQuery()  
 コマンドを実行しますが、何も返しません。 このメソッドは、クエリ以外のコマンド (何も返さないコマンド) を実行する場合に便利です。 たとえば、アップデートグラムや DiffGram でレコードを更新し、何も返さない場合に使用できます。  
  
 Stream ExecuteStream()  
 新しいストリーム オブジェクトを返します。 このメソッドは、クエリ結果を新しいストリームで返す場合に便利です。 作業用サンプルについては、次を参照してください。 [SQL クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md).  
  
 public void ExecuteToStream (Stream outputStream)  
 クエリ結果を既存のストリームに書き込みます。 このメソッドは、結果を (たとえば、クエリ結果が、System.Web.HttpResponse.OutputStream に書き込まれた) 追加する必要があるストリームがある場合に便利です。 作業用サンプルについては、次を参照してください。 [SQL クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md).  
  
 XmlReader ExecuteXmlReader()  
 XmlReader オブジェクトを返します。 このメソッドは、XmlReader オブジェクト内のデータを直接操作または可能 System.Xml のアーキテクチャでは、接続のいずれかを使用することができます。 詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のドキュメントを参照してください。 作業用サンプルについては、次を参照してください。 [ExecuteXMLReader メソッドを使用して SQL クエリを実行する](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)です。  
  
 TheSqlXmlCommand オブジェクトには、これらの追加メソッドもサポートしています。  
  
 SqlXmlParameter CreateParameter()  
 SqlXmlParameter オブジェクトを作成します。 値を設定することができます、*名前*と*値*このオブジェクトのパラメーターです。 このメソッドは、コマンドにパラメーターを渡す場合に便利です。 作業用サンプルについては、次を参照してください。 [SQL クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md).  
  
 void ClearParameters()  
 指定したコマンド オブジェクトに作成されたパラメーターを消去します。 このメソッドは、同一のコマンド オブジェクトで複数のクエリを実行する場合に便利です。  
  
## <a name="properties"></a>プロパティ  
 SqlXmlCommand オブジェクトには、これらのプロパティもサポートしています。  
  
 ClientSideXml  
 True に設定すると、サーバーではなくクライアント側で、行セットが XML に変換されます。 このプロパティは、パフォーマンスの負荷を中間層に移す場合に便利です。 このプロパティを使用すると、既存のストアド プロシージャを FOR XML でラップして XML に出力することもできます。  
  
 SchemaPath  
 マッピング スキーマの名前とディレクトリ パス (C:\x\y\MySchema.xml など) を指定します。 このプロパティは、XPath クエリにマッピング スキーマを指定するときに便利です。 パスは、相対パスまたは絶対パスで指定できます。 パスが相対パスでの相対パスを解決するのには基本パスで指定されている基本パスが使用されます。 基本パスが指定されていない場合、相対パスは現在のディレクトリからのパスになります。 作業用サンプルについては、次を参照してください。 [.NET 環境での SQLXML 機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)です。  
  
 XslPath  
 XSL ファイルの名前とディレクトリ パスを指定します。 パスは、相対パスまたは絶対パスで指定できます。 パスが相対パスでの相対パスを解決するのには基本パスで指定されている基本パスが使用されます。 基本パスが指定されていない場合、相対パスは現在のディレクトリからのパスになります。 作業用サンプルについては、次を参照してください[XSL 変換 & #40; を適用する。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 基本パス  
 基本パス (ディレクトリ パス) を指定します。 このプロパティは、XSL ファイル (を XslPath プロパティを使用)、(を SchemaPath プロパティを使用)、マッピング スキーマ ファイルまたは XML テンプレートの外部スキーマ参照に対して指定されている相対パスを解決するために便利です (を使用して指定された、 **マッピング スキーマ**属性)。  
  
 OutputEncoding  
 コマンドを実行したときに返されるストリームのエンコードを指定します。 このプロパティは、返されるストリームに特定のエンコードを要求する場合に便利です。 一般的に使用されるエンコードには、UTF-8、ANSI、Unicode などがあります。 既定のエンコードは UTF-8 です。  
  
 名前空間  
 名前空間を使用する XPath クエリの実行を有効にします。 名前空間を持つ XPath クエリの詳細については、次を参照してください[名前空間と #40 です。 使用する XPath クエリを実行する。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). 作業用サンプルについては、次を参照してください。 [XPath クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 コマンドを実行して生成される XML の、単一のルート要素を指定します。 有効な XML ドキュメントには、単一のルートレベルのタグが必要です。 このプロパティでは、コマンドを実行して単一の最上位要素のない XML フラグメントが生成された場合に、返される XML のルート要素を指定できます。 作業用サンプルについては、次を参照してください[XSL 変換 & #40; を適用する。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 コマンドのテキストを指定します。 このプロパティは、実行するコマンドのテキストを指定するときに使用します。 作業用サンプルについては、次を参照してください。 [SQL クエリの実行 & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md).  
  
 CommandStream  
 コマンド ストリームを指定します。 このプロパティは、XML テンプレートなどのファイルからコマンドを実行する場合に便利です。 CommandStream、のみを使用する場合 **"Template"**、 **"UpdateGram"** と **"DiffGram"CommandType**値はサポートされています。 作業用サンプルについては、次を参照してください。 [CommandStream プロパティを使用して、テンプレート ファイルを実行する](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)です。  
  
 CommandType  
 コマンドの種類を指定します。 このプロパティは、実行するコマンドの種類を指定するときに使用します。 コマンドの種類の値を、次の表に示します。 作業用サンプルについては、次を参照してください。 [.NET 環境での SQLXML 機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)です。  
  
|値|Description|  
|-----------|-----------------|  
|SqlXmlCommandType.Sql|SQL コマンド (`SELECT * FROM Employees FOR XML AUTO` など) を実行します。|  
|SqlXmlCommandType.XPath|XPath コマンド (`Employees[@EmployeeID=1]` など) を実行します。|  
|SqlXmlCommandType.Template|XML テンプレートを実行します。|  
|SqlXmlCommandType.TemplateFile|指定したパスにあるテンプレート ファイルを実行します。|  
|SqlXmlCommandType.UpdateGram|アップデート グラムを実行します。|  
|SqlXmlCommandType.Diffgram|DiffGram を実行します。|  
  
## <a name="see-also"></a>参照  
 [SqlXmlParameter オブジェクト & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [SqlXmlAdapter オブジェクト & #40 です。SQLXML マネージ クラス"&"#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
