---
title: "Excel 変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.exceldest.f1"
helpviewer_keywords: 
  - "変換先 [Integration Services]、Excel"
  - "Excel [Integration Services]"
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Excel 変換先
  Excel 変換先は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブックのワークシートまたは範囲にデータを読み込みます。  
  
## アクセス モード  
 Excel 変換先には、データを読み込むために、次の 3 つの異なるデータ アクセス モードが用意されています。  
  
-   テーブルまたはビュー。  
  
-   変数で指定されたテーブルまたはビュー。  
  
-   SQL ステートメントの結果。 クエリにはパラメーター化クエリを使用できます。  
  
> [!IMPORTANT]  
>  Excel でのワークシートまたは範囲は、テーブルまたはビューに相当します。 Excel ソース エディターと Excel 変換先エディターで使用できるテーブルの一覧では、既存のワークシート (Sheet1$ など、ワークシート名に $ 記号を付加して識別) と名前付き範囲 (MyRange など、$ 記号が付かないことで識別) のみが表示されます。  
  
## 使用に関する注意点  
 Excel 接続マネージャーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 と、それによってサポートされる Excel ISAM (Indexed Sequential Access Method) ドライバーを使用して Excel データ ソースに接続し、データの読み取りおよび書き込みを行います。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報に含まれる資料の多くは、このプロバイダーおよびドライバーの処理に関するドキュメントです。これらの資料は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または従来のデータ変換サービスに固有のものではありませんが、予期しない結果が発生する可能性のある特定の動作について知っておくことをお勧めします。 Excel ドライバーの使用方法や動作に関する一般的な情報については、「 [[HOWTO] Visual Basic または VBA から ADO を Excel データで使用する](http://support.microsoft.com/kb/257819)」を参照してください。  
  
 Excel ドライバーに含まれる Jet プロバイダーの次のような動作が原因で、Excel 変換先にデータを保存するときに予期しない結果が発生する場合があります。  
  
-   **テキスト データの保存**。 Excel ドライバーでテキスト データの値を Excel 変換先に保存するときに、保存される値が確実にテキスト値として解釈されるように、ドライバーによって各セルに単一引用符が追加されます。 保存されたデータの読み取りや処理を行う他のアプリケーションがあるか、または開発する場合、各テキスト値の前に付けられた単一引用符に対する特殊な処理を含める必要があります。  
  
     単一引用符が含まれることを回避する方法については、msdn.com のブログ投稿「 [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package (SSIS パッケージで Excel 変換先データ フロー コンポーネントを使用すると、データが Excel に変換されるときに、すべての文字列に単一引用符が追加される)](http://go.microsoft.com/fwlink/?LinkId=400876)」を参照してください。  
  
-   **メモ (ntext) データの保存**。 255 文字を超える文字列を Excel 列に正常に保存するには、変換先の列のデータ型を **文字列型** ではなく **メモ型**としてドライバーが認識する必要があります。 変換先のテーブルに既にデータ行が含まれている場合、ドライバーによってサンプリングされた先頭の数行のメモ列に、255 文字を超える値のインスタンスが 1 つ以上含まれている必要があります。 変換先のテーブルがパッケージの設計時または実行時に作成される場合は、CREATE TABLE ステートメントで LONGTEXT (またはそのいずれかのシノニム) をメモ列のデータ型として使用する必要があります。  
  
-   **データ型**。 Excel ドライバーでは、データ型の限定されたセットのみを認識します。 たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、Excel データ型を次のようにマップします。  
  
    -   Numeric – 倍精度浮動小数点数 (DT_R8)  
  
    -   Currency – 通貨 (DT_CY)  
  
    -   Boolean – ブール (DT_BOOL)  
  
    -   Date/time – **日付** (DT_DATE)  
  
    -   String – Unicode 文字列、長さ 255 (DT_WSTR)  
  
    -   Memo – Unicode テキスト ストリーム (DT_NTEXT)  
  
-   **データ型と長さの変換**。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、データ型の暗黙的な変換は行われません。 したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel データを Excel 以外のデータに変換してから Excel 変換先に読み込む必要があります。 この場合、初期パッケージを作成する際に、必要な変換を構成できるインポート ウィザードおよびエクスポート ウィザードを使用すると便利な場合があります。 必要な変換の例を次に示します。  
  
    -   特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換  
  
    -   255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換  
  
    -   倍精度の Excel 数値列と他の型の数値列の列間の変換  
  
## Excel 変換先の構成  
 Excel 変換先は、Excel 接続マネージャーを使用してデータ ソースに接続します。Excel 接続マネージャーでは、使用する Excel ブック ファイルを指定します。 詳しくは、「 [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md)」をご覧ください。  
  
 Excel 変換先は、1 つの標準入力と 1 つのエラー出力をとります。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[Excel 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[Excel 変換先エディター] ([接続マネージャー] ページ)](../Topic/Excel%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [[Excel 変換先エディター] ([マッピング] ページ)](../Topic/Excel%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [[Excel 変換先エディター] ([エラー出力] ページ)](../Topic/Excel%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるすべてのプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [Excel のカスタム プロパティ](../../integration-services/data-flow/excel-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## 関連タスク  
  
-   [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## 関連コンテンツ  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 1/3): 接続とコンポーネント](http://go.microsoft.com/fwlink/?LinkId=217674)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 2/3): テーブルとデータ型](http://go.microsoft.com/fwlink/?LinkId=217675)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 3/3): 問題点と対処法](http://go.microsoft.com/fwlink/?LinkId=217676)」  
  
## 参照  
 [Excel ソース](../../integration-services/data-flow/excel-source.md)   
 [Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)   
 [データ フロー](../../integration-services/data-flow/data-flow.md)   
 [スクリプト タスクを使用した Excel ファイルの操作](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  