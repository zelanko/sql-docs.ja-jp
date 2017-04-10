---
title: "Foreach ループ コンテナー | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.foreachloopcontainer.f1"
  - "sql13.dts.designer.foreachloopcontainer.general.f1"
  - "sql13.dts.designer.foreachloopcontainer.collection.f1"
  - "sql13.dts.designer.foreachloopcontainer.mapping.f1"
  - "sql13.dts.designer.schemarestrictions.f1"
  - "sql13.dts.designer.foreachitemcolumns.f1"
  - "sql13.dts.designer.selectsmoenumeration.f1"
helpviewer_keywords: 
  - "repeating control flow"
  - "Foreach Loop containers"
  - "foreach enumerators [Integration Services]"
  - "containers [Integration Services], Foreach Loop"
ms.assetid: dd6cc2ba-631f-4adf-89dc-29ef449c6933
caps.latest.revision: 73
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 72
---
# Foreach ループ コンテナー
  Foreach ループ コンテナーは、パッケージ内で繰り返す制御フローを定義します。 ループの実装は、プログラミング言語の **Foreach** ループ構造と同様です。 パッケージでは、ループは Foreach 列挙子を使用することで有効になります。  Foreach ループ コンテナーは、指定した列挙子のメンバーが処理されるたびに制御フローを繰り返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、次の種類の列挙子が用意されています。  
  
-   Foreach ADO 列挙子は、テーブル内の行を列挙します。 たとえば、ADO レコードセット内の行を取得できます。  
  
     レコードセット変換先では、 **Object** データ型のパッケージ変数に格納されるレコードセットのメモリにデータが保存されます。 通常は、Foreach ループ コンテナーと Foreach ADO 列挙子を使用して、一度に 1 つのレコードセット行を処理します。 Foreach ADO 列挙子に指定する変数は、Object データ型である必要があります。 レコードセット変換先の詳細については、「 [Use a Recordset Destination](../../integration-services/data-flow/use-a-recordset-destination.md)」を参照してください。  
  
-   Foreach ADO.NET Schema Rowset 列挙子は、データ ソースに関するスキーマ情報を列挙します。 たとえば、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内のテーブルを列挙して一覧を取得できます。  
  
-   Foreach File 列挙子は、フォルダー内のファイルを列挙します。 この列挙子は、サブフォルダーをスキャンできます。 たとえば、Windows フォルダーとそのサブフォルダー内から、ファイル名に拡張子 *.log が付いたファイルをすべて読み取ることができます。  
  
-   Foreach From Variable 列挙子は、指定した変数に含まれる列挙可能なオブジェクトを列挙します。 列挙可能なオブジェクトは、配列、ADO.NET **DataTable**、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 列挙子などです。 たとえば、サーバーの名前を含む配列の値を列挙できます。  
  
-   Foreach Item 列挙子は、コレクション内のアイテムを列挙します。 たとえば、プロセス実行タスクで使用する実行可能ファイルおよび作業ディレクトリの名前を列挙できます。  
  
-   Foreach Nodelist 列挙子は、XML パス言語 (XPath) 式の結果セットを列挙します。 たとえば、 `/authors/author[@period='classical']`の式は、古典時代のすべての作家を列挙して一覧を取得します。  
  
-   Foreach SMO 列挙子は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) オブジェクトを列挙します。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内のビューを列挙して一覧を取得できます。  
  
-   Foreach HDFS ファイル列挙子は、指定した HDFS の場所にある HDFS ファイルを列挙します。  
  
-   Foreach Azure BLOB 列挙子は、Azure Storage の BLOB コンテナーで BLOB を列挙します。  
  
 次の図は、ファイル システム タスクを含む Foreach ループ コンテナーを示しています。 Foreach ループは Foreach File 列挙子を使用し、ファイル システム タスクがファイルをコピーするように構成します。 列挙子が指定するフォルダーに 4 つのファイルが含まれる場合、ループが 4 回繰り返されて 4 つのファイルがコピーされます。  
  
 ![フォルダーを列挙する Foreach ループ コンテナー](../../integration-services/control-flow/media/ssis-foreachloop.gif "フォルダーを列挙する Foreach ループ コンテナー")  
  
 変数とプロパティ式を組み合わせて使用すると、パッケージ オブジェクトのプロパティを列挙子のコレクションの値で更新できます。 最初にコレクションの値をユーザー定義変数にマップし、次に、変数を使用するプロパティにプロパティ式を実装します。 たとえば、Foreach File 列挙子のコレクションの値を **MyFile** という変数にマップし、次に、この変数をメール送信タスクの Subject プロパティのプロパティ式で使用します。 パッケージを実行すると、Subject プロパティは、ループが繰り返されるたびにファイルの名前で更新されます。 詳細については、「[パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」をご覧ください。  
  
 列挙子のコレクションの値にマップされた変数は、式とスクリプトでも使用できます。  
  
 Foreach ループ コンテナーには複数のタスクとコンテナーを含めることができますが、使用できる列挙子は 1 種類のみです。 Foreach ループ コンテナーに複数のタスクが含まれる場合、列挙子のコレクションの値は各タスクの複数のプロパティにマップできます。  
  
 Foreach ループ コンテナー上でトランザクションの属性を設定し、パッケージ制御フローのサブセットのトランザクションを定義できます。 この方法により、トランザクションをパッケージ レベルではなく Foreach ループ レベルで管理できます。 たとえば、Foreach ループ コンテナーが、スター スキーマ内のディメンション テーブルおよびファクト テーブルを更新する制御フローを繰り返す場合、トランザクションを構成して、すべてのファクト テーブルが正しく更新されるようにしたり、ファクト テーブルを更新しないようにすることができます。 詳細については、「[Integration Services のトランザクション](../../integration-services/integration-services-transactions.md)」をご覧ください。  
  
## 列挙子の種類  
 列挙子は構成可能ですが、列挙子に応じて、それぞれ異なる情報を指定する必要があります。  
  
 次の表に、各種列挙子で必要な情報の概要を示します。  
  
|列挙子|構成要件|  
|----------------|--------------------------------|  
|Foreach ADO|ADO オブジェクトの基になる変数と、列挙子モードを指定します。 変数は、Object データ型である必要があります。|  
|Foreach ADO.NET Schema Rowset|データベースへの接続と、列挙するスキーマを指定します。|  
|Foreach File|フォルダーと、列挙するファイル、取得するファイルのファイル名の形式、およびサブフォルダーをスキャンするかどうかを指定します。|  
|Foreach From Variable|列挙するオブジェクトが含まれる変数を指定します。|  
|Foreach Item|列や列のデータ型など、Foreach Item コレクション内のアイテムを定義します。|  
|Foreach Nodelist|XML ドキュメントの基になる XML ドキュメントを指定し、XPath 操作を構成します。|  
|Foreach SMO|データベースへの接続と、列挙する SMO オブジェクトを指定します。|  
|Foreach HDFS File Enumerator (Foreach HDFS ファイル列挙子)|フォルダーと、列挙するファイル、取得するファイルのファイル名の形式、およびサブフォルダーをスキャンするかどうかを指定します。|  
|Foreach Azure BLOB|列挙する BLOB を含む Azure BLOB コンテナーを指定します。|  
  
## Foreach ループ コンテナー内のプロパティ式  
 パッケージは、複数の実行可能ファイルが同時に実行されるように構成できます。 プロパティ式を実装した Foreach ループ コンテナーがパッケージに含まれるときは、この構成を注意して使用する必要があります。  
  
 多くの場合、Foreach ループ列挙子が使用する接続マネージャーの ConnectionString プロパティの値を設定するには、プロパティ式を実装すると便利です。 ConnectionString のプロパティ式は、列挙子のコレクションの値にマップした変数によって設定され、ループの反復ごとに更新されます。  
  
 ループ内のタスクの並列実行が非決定的なタイミングで行われるという不適切な結果を回避するには、一度に 1 つしか実行可能ファイルが実行されないようにパッケージを構成する必要があります。 たとえば、パッケージが同時に複数のタスクを実行できる場合、フォルダー内のファイルを列挙する Foreach ループ コンテナーでファイル名を取得してから SQL 実行タスクを使用してテーブルにファイル名を挿入すると、SQL 実行タスクの 2 つのインスタンスが同時に書き込もうとして、書き込みの競合が発生する可能性があります。 詳細については、「[パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」をご覧ください。  
  
## 関連タスク  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 
              [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [Foreach ループ コンテナーを構成する](../Topic/Configure%20a%20Foreach%20Loop%20Container.md)  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
## 関連コンテンツ  
 bidn.com のブログ「 [SSIS の For Each ノード一覧の列挙子](http://go.microsoft.com/fwlink/?LinkId=220671)」  
  
## 参照  
 [制御フロー](../../integration-services/control-flow/control-flow.md)   
 [Integration Services コンテナー](../../integration-services/control-flow/integration-services-containers.md)  
  
  