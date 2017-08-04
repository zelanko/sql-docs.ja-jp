---
title: "CDC ソースを使用して変更データを抽出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 343efa882f37276c6921edc72d2bf1e615ff1a18
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="extract-change-data-using-the-cdc-source"></a>CDC ソースを使用した変更データ抽出
  CDC ソースを追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの CDC 制御タスクがあらかじめ含まれている必要があります。  
  
 CDC 制御タスクの操作の詳細については、「 [CDC 制御タスク](../../integration-services/control-flow/cdc-control-task.md)」を参照してください。  
  
 CDC ソースの詳細については、「 [CDC ソース](../../integration-services/data-flow/cdc-source.md)」を参照してください。  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a>CDC ソースを使用して変更データを抽出するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、次に **[ツールボックス]**で、CDC ソースをデザイン画面にドラッグします。  
  
4.  CDC ソースをダブルクリックします。  
  
5.  **[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、一覧から既存の ADO.NET 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。 読み取る変更テーブルが含まれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続であることが必要です。  
  
6.  変更を処理する **[CDC テーブル]** を選択します。  
  
7.  読み取る CDC テーブルの **CDC キャプチャ インスタンス** の名前を選択または入力します。  
  
     キャプチャされたソース テーブルには、スキーマの変更によりテーブル定義のシームレスな遷移を処理するためのキャプチャされたインスタンスが 1 ～ 2 個含まれることがあります。 キャプチャ対象のソース テーブルに複数のキャプチャ インスタンスが定義されている場合は、ここで使用するキャプチャ インスタンスを選択してください。 [スキーマ] のテーブルの既定のキャプチャ インスタンス名。[テーブル] は\<スキーマ > _\<テーブル > が、使用中の実際のキャプチャ インスタンス名が異なる場合があります。 読み取られた実際のテーブルが CDC テーブル**cdc\< 。キャプチャ インスタンス > _CT**です。  
  
8.  処理上のニーズに最も適した処理モードを選択します。 オプションは次のとおりです。  
  
    -   **[すべて]**: **[更新前]** の値なしで、現在の CDC 範囲内の変更を返します。  
  
    -   **[古い値を含むすべて]**: 古い値 (**[更新前]**) を含め、現在の CDC 処理範囲内の変更を返します。 更新操作ごとに、2 つの行 (更新前の値の行と更新後の値の行) が存在することになります。  
  
    -   **[差分]**: 現在の CDC 処理範囲内で変更された、ソース行あたり 1 つの変更行のみを返します。 ソース行が複数回更新された場合は、変更が結合されたうえで生成されます (たとえば、挿入と更新が 1 回の更新として、または更新と削除が 1 回の削除として、結合されたうえで生成されることがあります)。 [差分] 変更処理モードで作業する場合は、1 つのソース行が複数の出力に出現するため、変更を削除、挿入、および更新の各出力に分割し、並行処理することができます。  
  
    -   **更新マスクを持つ net**: このモードは、通常 [差分] モードに似ていますが、名前のパターンを持つブール型の列も追加**_ _ $\<列名 >\__Changed**現在の変更された列が行を変更することを示すです。  
  
    -   **[結合を含む差分]**: このモードは通常の [結合] モードと似ていますが、挿入操作と更新操作が 1 つの結合操作 (UPSERT) に結合されます。  
  
9. 現在の CDC コンテキストの CDC 状態を保持する SSIS 文字列パッケージ変数を選択します。 CDC 状態変数の詳細については、「 [状態変数の定義](../../integration-services/data-flow/define-a-state-variable.md)」を参照してください。  
  
10. **__$reprocessing** という特別な出力列を作成する場合は、 **[再処理インジケーター列を含める]**チェック ボックスをオンにします。 CDC 処理範囲が初期処理範囲 (初期読み込みの期間に対応する LSN の範囲) と重なる場合か、CDC 処理範囲が前の実行でのエラーの後に再処理される場合、この列の値は **true** になります。 このインジケーター列を使用すると、SSIS 開発者は変更を再処理するときに、エラーを別々に処理できます (たとえば、非既存行の削除やキーの重複により失敗した挿入などの操作を無視できます)。  
  
     詳細については、「 [CDC ソースのカスタム プロパティ](../../integration-services/data-flow/cdc-source-custom-properties.md)」を参照してください。  
  
11. 外部列と出力列間のマッピングを更新するには、 **[列]** をクリックし、 **[外部列]** 一覧にある別の列を選択します。  
  
12. 必要に応じて、 **[出力列]** 一覧の値を削除し、出力列の値を更新します。  
  
13. エラー出力を構成するには、 **[エラー出力]**をクリックします。  
  
14. **[プレビュー]** をクリックすると、CDC ソースによって抽出されるデータを最大 200 行表示できます。  
  
15. **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [CDC ソース エディター &#40;[接続マネージャー] ページ&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../../integration-services/data-flow/cdc-source-editor-columns-page.md)   
 [CDC ソース エディターと &#40; です。エラー出力 ページと &#41; です。](../../integration-services/data-flow/cdc-source-editor-error-output-page.md)  
  
  
