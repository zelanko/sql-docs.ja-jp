---
title: "OLE DB 変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.oledbdest.f1"
helpviewer_keywords: 
  - "高速読み込みデータ アクセス モード [Integration Services]"
  - "OLE DB 変換先 [Integration Services]"
  - "高速読み込みオプション [Integration Services]"
  - "読み込みオプション、高速 [Integration Services]"
  - "変換先 [Integration Services]、OLE DB"
  - "高速読み込みデータ アクセス モード [Integration Services]"
  - "挿入、データ"
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
caps.latest.revision: 79
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 79
---
# OLE DB 変換先
  OLE DB 変換先は、データベースのテーブルやビュー、または SQL コマンドを使用して、OLE DB に準拠するさまざまなデータベースにデータを読み込みます。 たとえば、OLE DB ソースにより、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースのテーブルにデータを読み込むことができます。  
  
> [!NOTE]  
>  データ ソースが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 である場合、Excel の以前のバージョンとは異なる接続マネージャーが必要になります。 詳細については、「[Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)」を参照してください。  
  
 OLE DB 変換先には、データを読み込むために、次の 5 つの異なるデータ アクセス モードが用意されています。  
  
-   テーブルまたはビュー。 既存のテーブルまたはビューを指定できます。または、新しいテーブルを作成できます。  
  
-   テーブルまたはビュー (高速読み込みオプションを使用)。 既存のテーブルを指定できます。または新しいテーブルを作成できます。  
  
-   変数で指定されたテーブルまたはビュー。  
  
-   変数で指定されたテーブルまたはビュー (高速読み込みオプションを使用)。  
  
-   SQL ステートメントの結果。  
  
> [!NOTE]  
>  OLE DB 変換先ではパラメーターがサポートされません。 パラメーター化された INSERT ステートメントを実行する必要がある場合は、OLE DB コマンド変換を検討してください。 詳細については、「 [OLE DB Command Transformation](../../integration-services/data-flow/transformations/ole-db-command-transformation.md)」を参照してください。  
  
 OLE DB 変換先で 2 バイト文字セット (DBCS) を使用するデータを読み込む際に、データ アクセス モードで高速読み込みオプションを使用せず、OLE DB 接続マネージャーが [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB) を使用している場合、そのデータは破損する可能性があります。 DBCS データの整合性を保持するには、OLE DB 接続マネージャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用するように構成するか、**[テーブルまたはビュー - 高速読み込み]** または **[テーブル名またはビュー名の変数 - 高速読み込み]** のうちいずれかの高速読み込みモードを使用する必要があります。 どちらのオプションも、**[OLE DB 変換先エディター]** ダイアログ ボックスから使用できます。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] オブジェクト モデルをプログラミングするときは、AccessMode プロパティを **[OpenRowset での FastLoad の使用]** または **[Variable から FastLoad を使用して OpenRowset]** に設定する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの **[OLE DB 変換先エディター]** ダイアログ ボックスを使用して、OLE DB 変換先がデータを挿入する変換先テーブルを作成する際に、新しく作成したテーブルを手動で選択する必要がある場合があります。 手動で選択する必要があるのは、OLE DB provider for DB2 などの OLE DB プロバイダーが、スキーマの識別子を自動的にテーブル名に追加した場合です。  
  
> [!NOTE]  
>  変換先の種類に応じて、**[OLE DB 変換先エディター]** ダイアログ ボックスによって生成される CREATE TABLE ステートメントの変更が必要になる場合があります。 たとえば、変換先によっては CREATE TABLE ステートメントで使用されるデータ型をサポートしない場合もあります。  
  
 OLE DB 変換先は、OLE DB 接続マネージャーを使用してデータ ソースに接続します。OLE DB 接続マネージャーでは、使用する OLE DB プロバイダーを指定します。 詳細については、「[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトでは、OLE DB 接続マネージャーを作成できるデータ ソース オブジェクトも用意されています。このオブジェクトは、データ ソースとデータ ソース ビューを OLE DB 変換先で使用できるようにします。  
  
 OLE DB 変換先には、入力列と変換先データ ソースの列との間のマッピングが含まれています。 入力列をすべての変換先列にマップする必要はありませんが、変換先列のプロパティによっては、変換先列にマップされる入力列がない場合、エラーが発生することがあります。 たとえば、入力先列で NULL 値が許容されていない場合は、入力列をその列にマップする必要があります。 また、マップされる列のデータ型には互換性がある必要があります。 たとえば、文字列データ型の入力列を数値データ型の変換先列にマップすることはできません。  
  
 OLE DB 変換先は、1 つの標準入力と 1 つのエラー出力をとります。  
  
 データ型の詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 高速読み込みオプション  
 OLE DB 変換先で高速読み込みデータ アクセス モードが使用される場合、**[OLE DB 変換先エディター]** のユーザー インターフェイスで、変換先に対して次の高速読み込みオプションを指定できます。  
  
-   インポートしたデータ ファイルの ID 値を保持します。または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられた一意の値を使用します。  
  
-   一括読み込み操作中に、NULL 値を保持します。  
  
-   一括インポート操作中に、インポート先のテーブルまたはビューに対して CHECK 制約を実行します。  
  
-   一括読み込み操作中に、テーブルレベルのロックを取得します。  
  
-   バッチの行数およびコミット サイズを指定します。  
  
 一部の高速読み込みオプションは、OLE DB 変換先の特定のプロパティに格納されています。 たとえば、ID 値を保持するかどうかを指定する FastLoadKeepIdentity、NULL 値を保持するかどうかを指定する FastLoadKeepNulls、バッチとしてコミットする行数を指定する FastLoadMaxInsertCommitSize などがあります。 その他の高速読み込みオプションは、FastLoadOptions プロパティのコンマ区切りリストで格納されます。 OLE DB 変換先で、FastLoadOptions に格納されている高速読み込みオプションと **[OLE DB 変換先エディター]** ダイアログ ボックスに一覧表示されている高速読み込みオプションをすべて使用する場合は、このプロパティの値を **TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000** に設定します。 値 1000 を設定すると、1,000 行のバッチを使用するように変換先が構成されます。  
  
> [!NOTE]  
>  変換先で制約が失敗すると、FastLoadMaxInsertCommitSize で定義された行数のバッチ全体が失敗します。  
  
 **[OLE DB 変換先エディター]** ダイアログ ボックスで公開される高速読み込みオプションに加えて、**[詳細エディター]** ダイアログ ボックスで、FastLoadOptions プロパティに次の一括読み込みオプションを入力することにより、それらのオプションを使用するように OLE DB 変換先を構成できます。  
  
|高速読み込みオプション|Description|  
|----------------------|-----------------|  
|KILOBYTES_PER_BATCH|挿入するサイズを KB 単位で指定します。 このオプションの形式は、**KILOBYTES_PER_BATCH** = \<正の整数**>** です。|  
|FIRE_TRIGGERS|挿入テーブルでトリガーを起動するかどうかを指定します。 このオプションの形式は、**FIRE_TRIGGERS** です。 このオプションが指定されている場合は、トリガーが起動されます。|  
|ORDER|入力データの並べ替え方法を指定します。 このオプションの形式は、ORDER \<列名> ASC&#124;DESC です。 並べ替える列のリストには任意の数列を指定できます。並べ替え順序の指定は省略することもできます。 並べ替え順序を指定しなかった場合は、データを並べ替えないと見なして挿入操作が実行されます。<br /><br /> 注: ORDER オプションを使用してテーブル上のクラスター化インデックスに従って入力データを並べ替えると、パフォーマンスが向上する可能性があります。|  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] キーワードは慣例として通常は大文字で入力しますが、これらのキーワードの大文字小文字は区別されません。  
  
 高速読み込みオプションの詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
## OLE DB 変換先のトラブルシューティング  
 OLE DB 変換先による外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、OLE DB 変換先による外部データ ソースへのデータ保存に関するトラブルシューティングを行うことができます。 OLE DB 変換先による外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。 詳細については、「[パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
## OLE DB 変換先の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[OLE DB 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[OLE DB 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [[OLE DB 変換先エディター] &#40;[マッピング] ページ&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [[OLE DB 変換先エディター] &#40;[エラー出力] ページ&#41;](../Topic/OLE%20DB%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [OLE DB カスタム プロパティ](../../integration-services/data-flow/ole-db-custom-properties.md)  
  
 プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [OLE DB 変換先を使用してデータを読み込む](../../integration-services/data-flow/load-data-by-using-the-ole-db-destination.md)  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## 関連コンテンツ  
 [OLE DB ソース](../../integration-services/data-flow/ole-db-source.md)  
  
 [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)  
  
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  