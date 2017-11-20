---
title: "Excel ソース |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelsource.f1
- sql13.dts.designer.excelsourceadapter.connection.f1
- sql13.dts.designer.excelsourceadapter.columns.f1
- sql13.dts.designer.excelsourceadapter.erroroutput.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: e8b5878513b74faa8df5e7766762f2f7287ec7af
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="excel-source"></a>Excel ソース
  Excel ソースは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック内のワークシートまたは範囲からデータを抽出します。  
  
 Excel ソースでは、データを抽出するために、次の 4 つの異なるデータ アクセス モードが用意されています。  
  
-   テーブルまたはビュー。  
  
-   変数で指定されたテーブルまたはビュー。  
  
-   SQL ステートメントの結果。 クエリにはパラメーター化クエリを使用できます。  
  
-   変数に格納された SQL ステートメントの結果。  
  
> [!IMPORTANT]  
>  Excel でのワークシートまたは範囲は、テーブルまたはビューに相当します。 Excel ソース エディターと Excel 変換先エディターで使用できるテーブルの一覧では、既存のワークシート (Sheet1$ など、ワークシート名に $ 記号を付加して識別) と名前付き範囲 (MyRange など、$ 記号が付かないことで識別) が表示されます。 詳細については、「使用に関する注意点」を参照してください。  
  
 Excel ソースは、Excel 接続マネージャーを使用してデータ ソースに接続します。Excel 接続マネージャーでは、使用する Excel ブック ファイルを指定します。 詳しくは、「 [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md)」をご覧ください。  
  
 Excel ソースは、1 つの標準出力と 1 つのエラー出力をとります。  
  
## <a name="usage-considerations"></a>使用に関する注意点  
 Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 と、それによってサポートされる Excel ISAM (Indexed Sequential Access Method) ドライバーを使用して Excel データ ソースに接続し、データの読み取りおよび書き込みを行います。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報に含まれる資料の多くは、このプロバイダーおよびドライバーの処理に関するドキュメントです。これらの資料は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または従来のデータ変換サービスに固有のものではありませんが、予期しない結果が発生する可能性のある特定の動作について知っておくことをお勧めします。 Excel ドライバーの使用方法や動作に関する一般的な情報については、「 [[HOWTO] Visual Basic または VBA から ADO を Excel データで使用する](http://support.microsoft.com/kb/257819)」を参照してください。  
  
 Jet プロバイダーを Excel ドライバーと共に使用した場合、次のような動作が原因で、Excel データ ソースのデータを読み取るときに予期しない結果が発生する場合があります。  
  
-   **データ ソース**。 Excel ブックの変換元データには、ワークシートまたは名前付き範囲 (MyRange など) を使用できます。ワークシート名には $ 記号を付加する必要があります (Sheet1$ など)。 SQL ステートメントでは、$ 記号による構文エラーを回避するため、ワークシートの名前を [Sheet1$] などのように区切る必要があります。 クエリ ビルダーは、これらの区切り記号を自動的に付加します。 ワークシートまたは範囲を指定した場合、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、連続したセルのブロックを読み取ります。 したがって、ソース データには、タイトル行またはヘッダー行とデータ行との間に空の行を入れることはできません。  
  
-   **不足している値**。 Excel ドライバーは、指定した変換元の特定の行数 (既定では 8 行) を読み取り、各列のデータ型を推測します。 1 つの列に複数のデータ型が混在している可能性がある場合、特に数値データとテキスト データが混合している場合に、Excel ドライバーは数が多い方のデータ型を優先して判定し、それ以外のデータ型のデータが含まれるセルについては NULL 値を返します  (同数の場合は、数値型が優先されます)。Excel ワークシートでのセル書式のほとんどのオプションは、このデータ型の判定に影響しません。 Excel ドライバーのこの動作を変更するには、インポート モードを指定します。 インポート モードを指定するには、 **[プロパティ]** ウィンドウで、Excel 接続マネージャーの接続文字列内の拡張プロパティの値に **IMEX=1** を追加します。 詳細については、「 [[PRB] DAO の OpenRecordset を使用すると Excel の値として NULL が返される](http://support.microsoft.com/kb/194124)」をご覧ください。  
  
-   **切り捨てられたテキスト**。 Excel の列にテキスト データが含まているとドライバーが判定した場合、ドライバーはサンプリングした最も長い値に基づいて、データ型 (文字列またはメモ) を選択します。 ドライバーがサンプリングした行で 255 文字より長い値が検出されなかった場合、その列はメモ列ではなく、255 文字の文字列の列として扱われます。 このため、255 文字より長い値があると、切り捨てられる場合があります。 切り捨てを発生させずにメモ列からデータをインポートするには、サンプリングされた行のうち 1 行以上のメモ列に、255 文字より長い値が含まれている状態にする必要があります。または、そのような行が含まれるように、ドライバーがサンプリングする行数を増やす必要があります。 サンプリングする行数を増やすには、 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** レジストリ キーの **TypeGuessRows** の値を増やします。 詳細については、「 [[PRB] DTS: Jet 4.0 OLEDB からの転送がバッファーのオーバーフロー エラーで失敗](http://support.microsoft.com/kb/281517)」をご覧ください。  
  
-   **データ型**。 Excel ドライバーでは、データ型の限定されたセットのみを認識します。 たとえば、すべての数値列は倍精度浮動小数点型 (DT_R8) として解釈され、すべての文字列の列 (メモ列以外) は 255 文字の Unicode 文字列 (DT_WSTR) として解釈されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、Excel データ型を次のようにマップします。  
  
    -   Numeric – 倍精度浮動小数 (DT_R8)  
  
    -   Currency – 通貨 (DT_CY)  
  
    -   Boolean – ブール (DT_BOOL)  
  
    -   Date/time – **日付** (DT_DATE)  
  
    -   String – Unicode 文字列、長さ 255 (DT_WSTR)  
  
    -   Memo – Unicode テキスト ストリーム (DT_NTEXT)  
  
-   **データ型と長さの変換**。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、データ型の暗黙的な変換は行われません。 したがって、派生列変換またはデータ変換の変換を使用して、Excel データを明示的に変換してから Excel 以外の変換先に読み込むか、Excel データを Excel 以外のデータに変換してから Excel 変換先に読み込む必要があります。 この場合、初期パッケージを作成する際に、必要な変換を構成できるインポート ウィザードおよびエクスポート ウィザードを使用すると便利な場合があります。 必要な変換の例を次に示します。  
  
    -   特定のコードページを使用した Unicode Excel 文字列の列と Unicode 以外の文字列の列間の変換  
  
    -   255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換  
  
    -   倍精度の Excel 数値列と他の型の数値列の列間の変換  
  
## <a name="excel-source-configuration"></a>Excel ソースの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるすべてのプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Excel のカスタム プロパティ](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)」をご覧ください。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [クエリ パラメーターをデータ フロー コンポーネントの変数にマップする](../../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [マージ変換およびマージ結合変換用にデータを並べ替える](../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [Excel をループ処理のファイルおよび Foreach ループ コンテナーを使用してテーブル](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
## <a name="excel-source-editor-connection-manager-page"></a>[Excel ソース エディター]\ ([接続マネージャー] ページ)
  **[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ノードを使用すると、変換元として [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ブックを選択して使用できます。 Excel ソースは、既存のブックのワークシートまたは名前付き範囲からデータを読み取ります。  
  
> [!NOTE]  
>  Excel ソースの **CommandTimeout** プロパティは **[Excel ソース エディター]**ではアクセスできませんが、 **[詳細エディター]**を使用して設定できます。 このプロパティの詳細については、「 [Excel のカスタム プロパティ](../../integration-services/data-flow/excel-custom-properties.md)」 の Excel ソースのセクションを参照してください。  
  
### <a name="static-options"></a>静的オプション  
 **OLE DB 接続マネージャー**  
 既存の Excel 接続マネージャーを一覧から選択するか、 **[新規作成]**をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[Excel 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。  
  
 **[データ アクセス モード]**  
 ソースからデータを選択する方法を指定します。  
  
|値|Description|  
|-----------|-----------------|  
|[テーブルまたはビュー]|Excel ファイルのワークシートまたは名前付き範囲からデータを取得します。|  
|[テーブル名またはビュー名の変数]|ワークシートまたは範囲の名前を変数に指定します。<br /><br /> **関連情報:** [パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|[SQL コマンド]|SQL クエリを使用して、Excel ファイルからデータを取得します。 |  
|[変数からの SQL コマンド]|SQL クエリ テキストを変数で指定します。|  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
### <a name="data-access-mode-dynamic-options"></a>データ アクセス モードの動的オプション  
  
#### <a name="data-access-mode--table-or-view"></a>[データ アクセス モード] = [テーブルまたはビュー]  
 **[Excel シートの名前]**  
 Excel ブックで使用できるワークシートまたは名前付き範囲の名前を一覧から選択します。  
  
#### <a name="data-access-mode--table-name-or-view-name-variable"></a>[データ アクセス モード] = [テーブル名またはビュー名の変数]  
 **[変数名]**  
 ワークシートまたは名前付き範囲の名前が含まれている変数を選択します。  
  
#### <a name="data-access-mode--sql-command"></a>[データ アクセス モード] = [SQL コマンド]  
 **[SQL コマンド テキスト]**  
 SQL クエリのテキストを入力し、 **[クエリの作成]**をクリックしてクエリを作成します。または、 **[参照]**をクリックし、クエリ テキストが含まれているファイルを参照します。  
  
 **パラメーター**  
 クエリ テキスト内でパラメーターのプレースホルダーとして "?" を使用することにより、 パラメーター化クエリを入力した場合は、 **[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、クエリ入力パラメーターをパッケージ変数にマップします。  
  
 **Build query**  
 SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。  
  
 **[参照]**  
 **[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。  
  
 **[クエリの解析]**  
 クエリ テキストの構文を検査します。  
  
#### <a name="data-access-mode--sql-command-from-variable"></a>データ アクセス モードが [変数からの SQL コマンド] の場合  
 **[変数名]**  
 SQL クエリのテキストを含む変数を選択します。  
  
## <a name="excel-source-editor-columns-page"></a>[Excel ソース エディター]\ ([列] ページ)
  **[Excel ソース エディター]** ダイアログ ボックスの **[列]** ページを使用すると、出力列をそれぞれの外部 (変換元) 列にマップできます。  
  
### <a name="options"></a>オプション  
 **使用できる外部列**  
 データ ソース内の使用できる外部列の一覧を表示します。 このテーブルを使用して列を追加または削除することはできません。  
  
 **外部列**  
 タスクで外部 (変換元) 列を読み取る順序を表示します。 この順序を変更するには、最初に上記のテーブル内で選択されている列を選択解除してから、一覧から外部列を別の順で選択します。  
  
 **出力列**  
 各出力列の一意な名前を表示します。 既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
## <a name="excel-source-editor-error-output-page"></a>[Excel ソース エディター]\ ([エラー出力] ページ)
  **[Excel ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。  
  
### <a name="options"></a>オプション  
 **入力または出力**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]**ページで選択した外部 (変換元) 列を表示します。  
  
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
  
## <a name="related-content"></a>関連コンテンツ  
  
-   hrvoje.piasevoli.com のブログ「 [Importing data from 64-bit Excel in SSIS](http://go.microsoft.com/fwlink/?LinkId=217673)」(SSIS での 64 ビット バージョンの Excel からのデータ インポート)  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 1/3): 接続とコンポーネント](http://go.microsoft.com/fwlink/?LinkId=217674)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 2/3): テーブルとデータ型](http://go.microsoft.com/fwlink/?LinkId=217675)」  
  
-   dougbert.com のブログ「 [Integration Services における Excel (パート 3/3): 問題点と対処法](http://go.microsoft.com/fwlink/?LinkId=217676)」  
  
  

