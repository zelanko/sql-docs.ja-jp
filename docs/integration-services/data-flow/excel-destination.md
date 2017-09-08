---
title: "移行先の excel |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.exceldest.f1
- sql13.dts.designer.exceldestadapter.connection.f1
- sql13.dts.designer.exceldestadapter.mappings.f1
- sql13.dts.designer.exceldestadapter.erroroutput.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 69a0a8b907fcb45cf6ecd0576fb6fba04775d237
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="excel-destination"></a>Excel 変換先
  Excel 変換先は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブックのワークシートまたは範囲にデータを読み込みます。  
  
## <a name="access-modes"></a>アクセス モード  
 Excel 変換先には、データを読み込むために、次の 3 つの異なるデータ アクセス モードが用意されています。  
  
-   テーブルまたはビュー。  
  
-   変数で指定されたテーブルまたはビュー。  
  
-   SQL ステートメントの結果。 クエリにはパラメーター化クエリを使用できます。  
  
> [!IMPORTANT]  
>  Excel でのワークシートまたは範囲は、テーブルまたはビューに相当します。 Excel ソース エディターと Excel 変換先エディターで使用できるテーブルの一覧では、既存のワークシート (Sheet1$ など、ワークシート名に $ 記号を付加して識別) と名前付き範囲 (MyRange など、$ 記号が付かないことで識別) のみが表示されます。  
  
## <a name="usage-considerations"></a>使用に関する注意点  
 Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 と、それによってサポートされる Excel ISAM (Indexed Sequential Access Method) ドライバーを使用して Excel データ ソースに接続し、データの読み取りおよび書き込みを行います。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報に含まれる資料の多くは、このプロバイダーおよびドライバーの処理に関するドキュメントです。これらの資料は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または従来のデータ変換サービスに固有のものではありませんが、予期しない結果が発生する可能性のある特定の動作について知っておくことをお勧めします。 Excel ドライバーの使用方法や動作に関する一般的な情報については、「 [[HOWTO] Visual Basic または VBA から ADO を Excel データで使用する](http://support.microsoft.com/kb/257819)」を参照してください。  
  
 Excel ドライバーに含まれる Jet プロバイダーの次のような動作が原因で、Excel 変換先にデータを保存するときに予期しない結果が発生する場合があります。  
  
-   **テキスト データの保存**。 Excel ドライバーでテキスト データの値を Excel 変換先に保存するときに、保存される値が確実にテキスト値として解釈されるように、ドライバーによって各セルに単一引用符が追加されます。 保存されたデータの読み取りや処理を行う他のアプリケーションがあるか、または開発する場合、各テキスト値の前に付けられた単一引用符に対する特殊な処理を含める必要があります。  
  
     単一引用符が含まれることを回避する方法については、msdn.com のブログ投稿「 [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package (SSIS パッケージで Excel 変換先データ フロー コンポーネントを使用すると、データが Excel に変換されるときに、すべての文字列に単一引用符が追加される)](http://go.microsoft.com/fwlink/?LinkId=400876)」を参照してください。  
  
-   **メモ (ntext) データの保存**。 255 文字を超える文字列を Excel 列に正常に保存するには、変換先の列のデータ型を **文字列型** ではなく **メモ型**としてドライバーが認識する必要があります。 変換先のテーブルに既にデータ行が含まれている場合、ドライバーによってサンプリングされた先頭の数行のメモ列に、255 文字を超える値のインスタンスが 1 つ以上含まれている必要があります。 変換先のテーブルがパッケージの設計時または実行時に作成される場合は、CREATE TABLE ステートメントで LONGTEXT (またはそのいずれかのシノニム) をメモ列のデータ型として使用する必要があります。  
  
-   **データ型**。 Excel ドライバーでは、データ型の限定されたセットのみを認識します。 たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、Excel データ型を次のようにマップします。  
  
    -   Numeric – 倍精度浮動小数点数 (DT_R8)  
  
    -   Currency – 通貨 (DT_CY)  
  
    -   Boolean – ブール (DT_BOOL)  
  
    -   Date/time –     **日付** (DT_DATE)  
  
    -   String – Unicode 文字列、長さ 255 (DT_WSTR)  
  
    -   Memo – Unicode テキスト ストリーム (DT_NTEXT)  
  
-   **データ型と長さの変換**。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、データ型の暗黙的な変換は行われません。 したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel データを Excel 以外のデータに変換してから Excel 変換先に読み込む必要があります。 この場合、初期パッケージを作成する際に、必要な変換を構成できるインポート ウィザードおよびエクスポート ウィザードを使用すると便利な場合があります。 必要な変換の例を次に示します。  
  
    -   特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換  
  
    -   255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換  
  
    -   倍精度の Excel 数値列と他の型の数値列の列間の変換  
  
## <a name="configuration-of-the-excel-destination"></a>Excel 変換先の構成  
 Excel 変換先は、Excel 接続マネージャーを使用してデータ ソースに接続します。Excel 接続マネージャーでは、使用する Excel ブック ファイルを指定します。 詳しくは、「 [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md)」をご覧ください。  
  
 Excel 変換先は、1 つの標準入力と 1 つのエラー出力をとります。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるすべてのプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Excel のカスタム プロパティ](../../integration-services/data-flow/excel-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 1/3): 接続とコンポーネント](http://go.microsoft.com/fwlink/?LinkId=217674)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 2/3): テーブルとデータ型](http://go.microsoft.com/fwlink/?LinkId=217675)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 3/3): 問題点と対処法](http://go.microsoft.com/fwlink/?LinkId=217676)」  
  
## <a name="excel-destination-editor-connection-manager-page"></a>[Excel 変換先エディター]\ ([接続マネージャー] ページ)
  **[Excel 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、データ ソース情報を指定したり、結果をプレビューしたりできます。 Excel 変換先では、 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ブックのワークシートまたは名前付き範囲にデータが読み込まれます。  
  
> [!NOTE]  
>  Excel 変換先の **CommandTimeout** プロパティは、 **[Excel 変換先エディター]**ではアクセスできませんが、 **[詳細エディター]**を使用して設定できます。 また、一部の高速読み込みオプションは **[詳細エディター]**でしか使用できません。 これらのプロパティの詳細については、「 [Excel Custom Properties](../../integration-services/data-flow/excel-custom-properties.md)」の「Excel 変換先」を参照してください。  
  
### <a name="static-options"></a>静的オプション  
 **Excel 接続マネージャー**  
 既存の Excel 接続マネージャーを一覧から選択するか、 **[新規作成]**をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[Excel 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。  
  
 **[データ アクセス モード]**  
 ソースからデータを選択する方法を指定します。  
  
|オプション|Description|  
|------------|-----------------|  
|[テーブルまたはビュー]|Excel データ ソースのワークシートまたは名前付き範囲にデータを読み込みます。|  
|[テーブル名またはビュー名の変数]|ワークシートまたは範囲の名前を変数に指定します。<br /><br /> **関連情報**: [パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|[SQL コマンド]|SQL クエリを使用して、Excel 変換先にデータを読み込みます。|  
  
 **[Excel シートの名前]**  
 ドロップダウン リストから Excel 変換先を選択します。 一覧が空の場合は **[新規]**をクリックします。  
  
 **[新規作成]**  
 **[新規]** をクリックすると、 **[テーブルの作成]** ダイアログ ボックスが表示されます。 **[OK]**をクリックすると、 **Excel 接続マネージャー** の参照先の Excel ファイルが作成されます。  
  
 **[既存のデータを表示]**  
 **[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
> [!WARNING]  
>  選択した **Excel 接続マネージャー** が存在しない Excel ファイルを参照している場合、このボタンをクリックするとエラー メッセージが表示されます。  
  
### <a name="data-access-mode-dynamic-options"></a>データ アクセス モードの動的オプション  
  
#### <a name="data-access-mode--table-or-view"></a>[データ アクセス モード] = [テーブルまたはビュー]  
 **[Excel シートの名前]**  
 データ ソースで使用できるワークシートまたは名前付き範囲の名前を一覧から選択します。  
  
#### <a name="data-access-mode--table-name-or-view-name-variable"></a>[データ アクセス モード] = [テーブル名またはビュー名の変数]  
 **[変数名]**  
 ワークシートまたは名前付き範囲の名前が含まれている変数を選択します。  
  
#### <a name="data-access-mode--sql-command"></a>[データ アクセス モード] = [SQL コマンド]  
 **[SQL コマンド テキスト]**  
 SQL クエリのテキストを入力し、 **[クエリの作成]**をクリックしてクエリを作成します。または、 **[参照]**をクリックし、クエリ テキストが含まれているファイルを指定します。  
  
 **[クエリの作成]**  
 SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。  
  
 **[参照]**  
 **[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。  
  
 **[クエリの解析]**  
 クエリ テキストの構文を検査します。  
  
## <a name="excel-destination-editor-mappings-page"></a>Excel 変換先エディター (マッピング ページ)
  **[Excel 変換先エディター]** ダイアログ ボックスの **[マッピング]** ページを使用すると、入力列を変換先列にマップできます。  
  
### <a name="options"></a>オプション  
 **使用できる入力列**  
 使用できる入力列の一覧を表示します。 ドラッグ アンド ドロップ操作により、テーブル内の使用できる入力列を変換先列にマップします。  
  
 **使用できる変換先列**  
 使用できる変換先列の一覧を表示します。 ドラッグ アンド ドロップ操作により、テーブル内の使用できる変換先列を入力列にマップします。  
  
 **入力列**  
 上の表で選択された入力列が表示されます。 **[使用できる入力列]**ボックスの一覧を使用して、マッピングを変更できます。  
  
 **変換先列**  
 マップされているかどうかに関係なく、使用できる変換先列を表示します。  
  
## <a name="excel-destination-editor-error-output-page"></a>[Excel 変換先エディター]\ ([エラー出力] ページ)
  **[Excel 変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理オプションを指定できます。  
  
### <a name="options"></a>オプション  
 **入力または出力**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]**ノードで選択されている外部 (ソース) 列を表示します。  
  
 **エラー**  
 エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **関連項目:** [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **切り捨て**  
 切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。  
  
 **Description**  
 エラーの説明を表示します。  
  
 **この値を選択したセルに設定します。**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **適用**  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="see-also"></a>参照  
 [Excel ソース](../../integration-services/data-flow/excel-source.md)   
 [Integration Services & #40 です。SSIS &#41;変数](../../integration-services/integration-services-ssis-variables.md)   
 [データ フロー](../../integration-services/data-flow/data-flow.md)   
 [スクリプト タスクを持つ Excel ファイルの操作](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
