---
title: "更新 - SQL Server ドキュメントの Advanced Analytics |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、Microsoft SQL Server の高度な分析のためのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fb6185aae04a1fb53a4db03cbab267e3f52dc779
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>新規または最近更新された: SQL Server の Advanced Analytics



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017-07-18** &nbsp;対&nbsp; **2017 年-09-11**
- *サブジェクト領域:* &nbsp; **for SQL Server の Advanced Analytics**です。

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

次のリンクは、最近追加された新しいアーティクルにジャンプします。


1. [リアルタイムのスコアリングまたは SQL Server のネイティブのスコア付けを実行する方法](r/how-to-do-realtime-scoring.md)
2. [事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。](r/install-pretrained-models-sql-server.md)
3. [ネイティブのスコアリング](sql-native-scoring.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この圧縮リストは、抜粋セクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [Python Machine Learning Services (In-database) を設定します。](#TitleNum_1)
2. [Revoscalepy の概要](#TitleNum_2)
3. [SQL Server のエディション間での Machine Learning 機能の相違点](#TitleNum_3)
4. [R コード (Machine Learning サービス) を使用できるように](#TitleNum_4)
5. [R Services のパフォーマンス: 結果とリソース](#TitleNum_5)
6. [R Services - データの最適化のパフォーマンス](#TitleNum_6)
7. [SQL Server の R パッケージの管理](#TitleNum_7)
8. [SQL Server Machine Learning サービス (データベース内) のセットアップ](#TitleNum_8)
9. [R で使用するための SQL Server の構成](#TitleNum_9)
10. [SQL Server で R のパフォーマンスの調整](#TitleNum_10)
11. [データ サイエンスのシナリオとソリューション テンプレート](#TitleNum_11)
12. [SQL Server の Machine Learning のサービスの新機能](#TitleNum_12)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-set-up-python-machine-learning-services-in-databasepythonsetup-python-machine-learning-servicesmd"></a>1.&nbsp;[Python Machine Learning Services (In-database) を設定](python/setup-python-machine-learning-services.md)

*最終更新日: 2017 年-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 263.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 fbe2ef55a5caecd64bb21ce854617a10b2d65567 8cd65baf77f27db00a0a4f07f3129a4231edb48b  (PR=3084  ,  Filename=setup-python-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=05976158e43d7dfafaf02289462d1537f5beeb36) -->



     [Modify the user account pool for SQL Server R Services--../r/modify-the-user-account-pool-for-sql-server-r-services.md)

SQL Server Standard Edition を使用しており、リソース ガバナーを持っていない場合は、サーバーのリソースを管理するための動的管理ビュー、および拡張イベントを使用できます。 また、この目的では、Windows イベントの監視を使用することができます。 詳細についてを参照してください [監視と管理 R Services--../r/managing-and-monitoring-r-solutions.md)。

**コンピューターをアップグレードするコンポーネントの学習**


SQL Server 2017 を使用して、マシン学習サービスをインストールするときに、リリースの公開時に、コンポーネントのバージョンを取得します。 修正プログラムを適用するか、SQL Server インスタンスをアップグレードするたびに、マシン学習コンポーネントは、アップグレードもします。

機械学習はサポートされているよりも高速なスケジュールでコンポーネントをアップグレードする Microsoft Machine Learning のサーバーをインストールすることによって、SQL Server のリリースでします。 これを行うときに取得することもなどの Machine Learning のサーバーの最新のリリースでサポートされている新しい機能。

+ 更新プログラム用 Python パッケージを[revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)と[for Python microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)です。
+ [モデルを事前トレーニング済み](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)イメージの分類とテキストの分析のためです。

インスタンスをアップグレードする方法については、[アップグレードの R コンポーネントをバインド--によって.. を参照してください。\r\use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)。

> [!NOTE]
>
> 現在のリリース バージョンには、machine learning のすべてのコンポーネントの最新バージョンが含まれています。 そのため、Microsoft Machine Learning サーバー経由でのアップグレードは、SQL Server 2017 のサポートされていますが、現在利用可能なアップグレードは SQL Server 2016 インスタンスにのみ適用されます。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>2.&nbsp;[Revoscalepy の概要](python/what-is-revoscalepy.md)

*最終更新日: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 79.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a d2eac3313a74bc5d5afd754fc357b3693e6801e1  (PR=2939  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



| (column_1) | (column_2) | (column_3) |
| :-- | :-- | :-- |
|`rx_btrees` | 確率的勾配ブースト デシジョン ツリーに合わせて|`rx_btrees_ex`CTP 2.0 で|
|`rx_dforest` | 適合するように分類と回帰のデシジョン フォレスト|`rx_dforest_ex`CTP 2.0 で|
|`rx_dtree` | 適合するように分類と回帰ツリー |`rx_dtree_ex`CTP 2.0 で|
|`rx_lin_mod` | 線形モデルを作成します。|`rx_lin_mod_ex`CTP 2.0 で|
|`rx_logit` | ロジスティック回帰モデルを作成する|`rx_logit_ex`CTP 2.0 で|
|`rx_predict` | トレーニング済みモデルから予測を生成します。|`rx_predict_ex`CTP 2.0 で|
|`rx_summary` | モデルの概要を生成します。||

Python のバージョンので新しい機械学習アルゴリズムが指定されても[MicrosoftML](https://docs.microsoft.com/en-us/r-server/python-reference/microsoftml/microsoftml-package):

| 関数| Description|
| ------ | ------ |
|`rx_fast_forest` |デシジョン フォレスト モデルを作成します。|
|`rx_fast_linear` | 確率的デュアル座標アセントを使用した線形回帰|
|`rx_fast_trees` | ブースト ツリー モデルを作成します。 |
|`rx_logistic_regression` | ロジスティック回帰モデルを作成する|
|`rx_neural_network` | カスタマイズ可能なニューラル ネットワーク モデルを作成します。 |
|`rx_oneclass_svm` | 異常検出で使用するための不均衡がデータセットに SVM モデルを作成します。|

> [!TIP]
> これらのアルゴリズムの多くは、Azure Machine Learning でモジュールとして既に提供します。

Python の MicrosoftML もなどが含まれるさまざまな変換およびヘルパー関数。

+ `rx_predict`トレーニング済みのモデルから予測を生成し、リアルタイムのスコアリングのために使用できます
+ イメージの特性付け関数
+ テキスト処理とセンチメント抽出関数

詳細については、「 [MicrosoftML の概要](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Python コミュニティは、何に使用される、すべて小文字のアルファベット、アンダー スコアではなくパラメーター名の camel 形式の組み合わせを含むよりも異なる可能性がありますコーディング規則を使用します。 また、状況によって異なる気付きかもを**revoscalepy**ライブラリは、常に小文字です。 その通りです！ Python の別の規則。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-differences-in-machine-learning-features-between-editions-of-sql-serverrdifferences-in-r-features-between-editions-of-sql-servermd"></a>3.&nbsp;[Machine learning の機能で SQL Server のエディションの違い](r/differences-in-r-features-between-editions-of-sql-server.md)

*最終更新日: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 47.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5890e212063f3ef228e69afe54e226320d2467f 4e0357701d960c0b8dbda1ac8d56a82f3335c77f  (PR=2964  ,  Filename=differences-in-r-features-between-editions-of-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



     Only Express Edition with Advanced Services includes the machine learning features. The performance limitations are similar to Standard Edition. Web edition is not intended for tasks such as creating machine learning models; however, you can use the PREDICT function to perform scoring using models trained elsewhere.

-   **Azure SQL データベース**

     R、Python スクリプトなど、マシン学習機能は現在は Azure SQL データベースでサポートされません。

     詳細についてとこの機能が利用可能なにある場合についてのお知らせは、SQL Server のブログを参照してください: [SQL Server 2017 の Python: データベース内の機械学習の強化](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


**すべてのエディションでサポートされている言語**


すべてのエディションは、次の machine learning 言語がサポートされています。

+ SQL Server 2017: R と Python
+ SQL Server 2016: R のみ

Microsoft R Open は、すべてのエディションに含まれます。



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-operationalize-r-code-machine-learning-servicesroperationalizing-your-r-codemd"></a>4.&nbsp; [を操作運用の R コード (Machine Learning サービス)](r/operationalizing-your-r-code.md)

*最終更新日: 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3) | [次](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e11d9a5db93932ec89ca96b5337aa4ea03c1d13 0779f06444b5b73ae2dff8bc190d0e388b4ae8e7  (PR=2660  ,  Filename=operationalizing-your-r-code.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



+ [リアルタイム--../リアルタイム回 scoring.md) 小さなバッチ用に最適化された、スコア付け
+ 単一の行をアプリケーションから呼び出すことのスコア付け
+ [ネイティブ スコアリング--../sql ネイティブ-scoring.md) で変更、R を呼び出さずに SQL Server の高速バッチ予測

このチュートリアルでは、バッチおよび単一行モードの両方でストアド プロシージャを使用してスコア付けの例を示します。

+ [R で SQL Server - データ サイエンスのチュートリアルを終了するには終了../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

これらのソリューション テンプレートをアプリケーションでスコアリングを統合する方法の例についてを参照してください。

+ [小売予測](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [不正行為の検出](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [顧客のクラスタ リング](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

**パフォーマンスの向上と小数点以下桁数**


オープン ソース R 言語は限界があることがわかって、RevoScaleR パッケージ Api 大規模なデータセットを処理でき恩恵をマルチ スレッド、マルチコア、マルチ プロセスのデータベース内計算できます。

場合、R ソリューションでは、複雑な集計を使用してまたは大規模なデータセットでは、SQL Server の効率的なインメモリ集計と列ストア インデックスを利用して R コードを使用できます統計の計算結果を処理し、スコア付けします。

SQL Server の Machine Learning でのパフォーマンスを向上させる方法の詳細についてを参照してください。

+ [パフォーマンス チューニングの SQL Server R Services--../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [パフォーマンスの最適化ヒントとテクニック](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**他のプラットフォーム用の R コードを改変または計算コンテキスト**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-performance-for-r-services-results-and-resourcesrperformance-case-study-r-servicesmd"></a>5.&nbsp;[R Services のパフォーマンス: 結果とリソース](r/performance-case-study-r-services.md)

*最終更新日: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_4) | [次](#TitleNum_6))

<!-- Source markdown line 282.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 40c8cd255ead88edc60531d45dd0377ecbaf7c9b eeca5eed96e2223508910b246dbff18173eecea3  (PR=2565  ,  Filename=performance-case-study-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



RevoScaleR と MicrosoftML の両方のパッケージは、大規模なデータセットを含む複雑な R ソリューションで予測モデルのトレーニングに使用されました。 SQL クエリと R コードは、同じでした。 インストールされる SQL server の 1 つの Azure VM ですべてのテストを実行しました。 作成者では、スコア付けの回および SQL Server によって提供されるこれらの最適化を使用せずに、比較。

- インメモリ テーブル
- ssNoVersion
- [リソース ガバナー]

R スクリプトの実行にソフト NUMA の影響を評価するためは、データ サイエンス チームは、Azure の仮想マシンを物理コア数を 20 にソリューションをテストします。 これらの物理コアの 4 つのソフト NUMA ノードは各ノードには、5 つのコアが含まれているように、自動的に作成されました。

CPU の結合は、シナリオでは、再開の一致、R ジョブへの影響の評価に適用されました。 4 つ**SQL のリソース プール**と 4 つ**外部リソース プール**作成されたと Cpu の同じセットの各ノードで使用することを確認してくださいに CPU 関係を指定しました。

各リソース プールは、ハードウェア使用率を最適化するために別のワークロード グループに割り当てられました。 その理由は、ソフト NUMA、CPU 関係は、物理 NUMA ノードの物理メモリを分けることはできません。そのため、定義で、同じ物理 NUMA ノードに基づくすべてのソフト NUMA ノード必要がありますメモリ使用 OS のメモリ ブロックは同じにします。 つまり、メモリ、プロセッサのアフィニティはありません。

次のプロセスが使用すると、この構成を作成します。

1. 既定では SQL Server に割り当てられたメモリの量を削減します。

2. R ジョブを並列で実行するための 4 つの新しいプールを作成します。

3. 各ワークロード グループはリソース プールに関連付けられているように、4 つのワークロード グループを作成します。

4. 新しいワークロード グループの割り当てとリソース ガバナーを再起動します。

5. ユーザー定義の分類子関数 (UDF) を割り当てる別のワークロード グループでさまざまなタスクを作成します。

6. 関数を使用して、適切なワークロード グループのリソース ガバナーの構成を更新します。



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-performance-for-r-services---data-optimizationrr-and-data-optimization-r-servicesmd"></a>6.&nbsp;[R Services - データの最適化のパフォーマンス](r/r-and-data-optimization-r-services.md)

*最終更新日: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_5) | [次](#TitleNum_7))

<!-- Source markdown line 107.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2ae2e54e8c5c8a3ec92fd2017088dd6ee879a9a1 9cb06bdce4ad6dfa2e9dc19da49103a6cd9817b3  (PR=2565  ,  Filename=r-and-data-optimization-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



> R Services が、テーブルからフェッチするために必要な列を決定する内部ヒューリスティックを使用して、テーブルがクエリではなく、データ ソースで指定されている場合ただし、この方法では、並列実行で発生する可能性はありません。

データを並列で分析できるためには、データベース エンジンが、並列クエリ プランを作成できるようにデータを取得するためのクエリを囲む必要があります。 コードまたはアルゴリズムは、大量のデータを使用している場合、以下のことを確認する指定されたクエリ`RxSqlServerData`並列実行に適しています。 並列実行プランにならないクエリは、計算の 1 つのプロセスになる可能性があります。

大規模なデータセットを使用する必要がある場合は、Management Studio や、R コードを実行する前に別の SQL クエリ アナライザーを使用して、実行プランを分析します。 クエリのパフォーマンスを向上させるためにすべての推奨手順を実行します。 たとえば、テーブルのインデックス不足は、クエリの実行時間に影響する可能性があります。 詳細については、[モニターとパフォーマンス--の調整] を参照してください。/../relational-databases/performance/monitor-and-tune-for-performance.md)。

パフォーマンスに影響する他のよくある間違いは、クエリが必要な数より多い列を取得します。 たとえば、数式は、3 つだけの列に基づいていますが、ソース テーブル内の 30 個の列が場合、データを不必要に移動します。

 + 使用しないでください`SELECT *`!
 + データセット内の列を確認し、分析に必要なものだけを識別する時間がかかる
 + GUID および rowguids などの R コードと互換性がないデータ型を含むすべての列に、クエリから削除します。
 + サポートされていない日付と時刻の形式の確認
 + テーブルを読み込むではなく特定の値を選択または変換エラーを回避する列をキャストするビューを作成します。

**機械学習アルゴリズムを最適化します。**


このセクションではその他のヒントと RevoScaleR と Microsoft R. に他のオプションに固有のリソース



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-r-package-management-for-sql-serverrr-package-management-for-sql-server-r-servicesmd"></a>7.&nbsp;[For SQL Server の R パッケージの管理](r/r-package-management-for-sql-server-r-services.md)

*最終更新日: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_6) | [次](#TitleNum_8))

<!-- Source markdown line 22.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2add5a7e1aef02487ac875e353c51161658050a4 5da92dd8b5402266a837172bda9aaabed3162ce8  (PR=2939  ,  Filename=r-package-management-for-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



このトピックでは、SQL Server のインスタンスで実行されている R パッケージの管理に使用できるパッケージの管理機能について説明します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

**T-SQL を使用してパッケージの管理**


Machine learning のジョブのサーバーを使用する場合は、これらの特権がある場合、コンピューターの管理者として R パッケージをインストールする続行することができます。

ただし、パッケージを他のユーザーと共有する必要がある場合、または複数の人が、サーバーで machine learning のジョブを実行する必要がある場合、パッケージの共有ライブラリを設定するより効率的です。 SQL Server では、データベース ロールを介して、これをサポートします。

データベース管理者は、ロールの設定、およびロールにユーザーを追加することを担当します。 ロールを介したデータベース管理者は追加または SQL Server 環境から R パッケージを削除するアクセス許可を持つユーザー、およびパッケージのインストールを監査することができますを制御できます。

**パッケージの管理用のデータベース ロール**


次の新しいデータベース ロールは、SQL Server のセキュリティで保護されたインストールし、R パッケージの管理をサポートします。

- `rpkgs-users`: すべてのメンバーによってインストールされた共有のパッケージを使用するユーザーをできるように、`rpkgs-shared`ロール。

- `rpkgs-private`: と同じ権限で共有のパッケージへのアクセスを提供する、`rpkgs-users`ロール。 このロールのメンバーは、プライベート スコープのパッケージをインストール、削除および使用することもできます。

-  `rpkgs-shared`: 同じアクセス許可を提供する、`rpkgs-private`ロール。 このロールのメンバーであるユーザーは、共有パッケージをインストールまたは削除することもできます。

- `db_owner`: 同じアクセス許可を持つ、`rpkgs-shared`ロール。 また、共有パッケージとプライベート パッケージの両方をインストールまたは削除する権利をユーザーに付与することもできます。

**T-SQL を使用して外部パッケージ ライブラリを作成します。**


さらに、T-SQL ステートメントをサポートしている SQL Server 2017**外部ライブラリの作成**、外部ライブラリのデータベース管理者による管理をサポートします。 現在このステートメントを使用して、Python パッケージや、Linux など、他のプラットフォームで実行用に作成されたパッケージの将来のサポートを計画し、r です。 追加の Windows ベースのライブラリを作成することができます。



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>8.&nbsp;[SQL Server マシン ラーニング Services (In-database) セットアップ](r/set-up-sql-server-r-services-in-database.md)

*最終更新日: 2017 年-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_7) | [次](#TitleNum_9))

<!-- Source markdown line 240.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 452dc36b4d0097f9562642238ba49eea0373d25b 4d355f6494b417dd90dce3943e7176eaece7336e  (PR=3070  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



データ サイエンス クライアント コンピューターで R ソリューションを作成し、計算コンテキストとして、SQL Server コンピューターを使用してコードを実行する必要がある場合は、SQL ログインまたは統合 Windows 認証を使用することができます。

* SQL ログインの場合は、読み取るデータが存在するデータベースに対する適切なアクセス許可をログインが持っていることを確認します。 できるように追加することで*への接続*と*選択*権限、またはへのログインを追加することで、 *db_datareader*ロール。 オブジェクトを作成する必要があるログインの場合は、追加*DDL_admin*権限です。 ログイン、テーブルにデータを保存する必要がありますを追加するログインの*db_datawriter*ロール。

* Windows 認証: インスタンス名とその他の接続情報を指定するデータ サイエンス クライアントに ODBC データ ソースを構成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)です。

**次の手順**


SQL Server で、スクリプトの実行機能が動作することを確認した後は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから R、Python のコマンドを実行できます。

ただし、いくつかは機械学習の頻繁に使用をサポートするか、新しい R パッケージを追加するには、システム構成を変更することができます。

このセクションでは、機械学習をサポートするために行えるいくつかの一般的な変更を一覧表示します。

**複数のワーカー アカウントを追加します。**


頻度の高い、R を使用すると思われる場合、または同時に実行中のスクリプトに多数のユーザーの予定の場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、[変更、ユーザー アカウント プールの SQL Server R Services--modify-the-user-account-pool-for-sql-server-r-services.md) を参照してください。

**<a name="bkmk_optimize"></a>外部スクリプトの実行用のサーバーを最適化します。**




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-sql-server-configuration-for-use-with-rrsql-server-configuration-r-servicesmd"></a>9.&nbsp;[R で使用するための SQL Server の構成](r/sql-server-configuration-r-services.md)

*最終更新日: 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_8) | [次](#TitleNum_10))

<!-- Source markdown line 149.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3f57bae70e3c118c1e2bcd57017322940bae83f8 f296242d470db47077cba4215ef420bd0c60bf33  (PR=2660  ,  Filename=sql-server-configuration-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



クエリでは、1 つのメモリ ノード (ノード 0) が返された場合は、ハードウェア NUMA、することはありませんか、ハードウェアがインターリーブ (非 NUMA) として構成されています。 SQL Server では、ハードウェア NUMA も無視されますと 4 つ以下の Cpu には、少なくとも 1 つのノードの CPU を 1 つだけの場合、または。

お使いのコンピューターが複数のプロセッサがハードウェア NUMA を持たない、使用することも[ソフト NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) Cpu をより小さなグループに分割します。  SQL Server 2016 および SQL Server 2017 で SQL Server サービスを開始するときに自動的に、ソフト NUMA 機能が有効です。

ソフト NUMA を有効にすると、SQL Server は、ノードを自動的を管理します。ただし、特定のワークロードの最適化を無効にできます_ソフト アフィニティ_し、ソフト NUMA ノードの CPU 関係を手動で構成します。 これは、ことができますかを制御するワークロードはどのノードに割り当てリソース管理をサポートする SQL Server のエディションを使用している場合に特にです。 CPU 関係を指定して、Cpu のグループを含むリソース プールの整列、によって、待機時間を短縮し、関連するプロセスが、同じ NUMA ノード内で実行されていることを確認できます。

ソフト NUMA と R ワークロードをサポートするために CPU 関係を構成するため、全体的なプロセスは次のとおりです。

1. 使用可能な場合は、ソフト NUMA を有効にします。
2. プロセッサのアフィニティを定義します。
3. [リソース ガバナー--.. を使用して、外部プロセス用のリソース プールを作成します。/r/resource-governance-for-r-services.md)
4. [ワークロード グループ--.. を割り当てる/../relational-databases/resource-governor/resource-governor-workload-group.md) を特定のアフィニティ グループ

サンプル コードを含む詳細については、このチュートリアルを参照してください: [SQL 最適化ヒントとテクニック (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**その他のリソース:**



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-performance-tuning-for-r-in-sql-serverrsql-server-r-services-performance-tuningmd"></a>10.&nbsp;[SQL Server で R のパフォーマンスの調整](r/sql-server-r-services-performance-tuning.md)

*最終更新日: 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_9) | [次](#TitleNum_11))

<!-- Source markdown line 76.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9c30753efdec81e499d5654b5b7a07f0cfe5b003 136a9f483bc8c9e1f69cf9d340d1472c21a52ec4  (PR=2565  ,  Filename=sql-server-r-services-performance-tuning.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



- 分散データベース エンジンの操作と R に SQL Server インスタンスを構成または Python スクリプトの適切なレベルで実行します。 これは、メモリと CPU 使用率、NUMA とプロセッサのアフィニティ設定、およびリソース グループの作成用の SQL Server の既定値の変更を含めることができます。

- 外部スクリプトの効率的な使用をサポートするために、サーバー コンピューターを最適化します。 これは、パッケージの管理を有効にすると、外部スクリプトの実行に使用されるアカウントの数を増やすことを含めることができ、関連するセキュリティ ロールを割り当てるユーザーをします。

- データの格納とインデックス作成など、SQL Server と統計戦略、クエリのデザインおよびクエリの最適化、および機械学習に使用されるテーブルのデザインに転送するには、特定の最適化を適用します。 データ ソースを分析することもあり、トランスポートのメソッド、または機能の展開を最適化するために、ETL プロセスを変更するデータ。

- 非効率性を避けるために分析モデルを調整します。 可能な最適化のスコープは、R コードおよびパッケージとを使用しているデータの複雑さによって異なります。 主なタスクには、コストの高いデータ変換を削除するか、タスクをオフロードするデータの準備や機能エンジニア リング R または Python から ETL プロセスまたは SQL が含まれます。 可能性がありますもスクリプトをリファクター、削除行でパッケージのインストールが、トレーニング、スコア付け、および evaluation、別のプロシージャに R コードを分割またはストアド プロシージャとして効率的に作業するためのコードを簡略化します。

**この系列内のアーティクル**


+ [パフォーマンスのチューニング SQL Server のハードウェアの R の..\r\sql-server-configuration-r-services.md)

    ハードウェアを構成するためのガイダンスを提供する '..'!テキストの NotShown--ssNoVersion_md--.\..\includes\ssnoversion-md.md)]、および外部スクリプトのサポートを向上させる SQL Server インスタンスを構成するためにインストールされます。 特に便利ですが**データベース管理者**です。

+ [SQL Server で R のパフォーマンスの調整のコードとデータの最適化--..\r\r-and-data-optimization-r-services.md)



&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-data-science-scenarios-and-solution-templatestutorialsdata-science-scenarios-and-solution-templatesmd"></a>11.&nbsp;[データ サイエンスのシナリオとソリューション テンプレート](tutorials/data-science-scenarios-and-solution-templates.md)

*最終更新日: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_10) | [次](#TitleNum_12))

<!-- Source markdown line 45.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 22c621731015f2192cb0b8d61b22062a4be50e70 6cf9e3f0a3803ed2bce9c4ffadfd7314f15f6b51  (PR=2964  ,  Filename=data-science-scenarios-and-solution-templates.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



[予測する方法とタイミング潜在顧客に連絡するには](https://microsoft.github.io/r-server-campaign-optimization/)

**新機能:**このソリューションでは、潜在顧客の人口統計、履歴応答データ、および製品固有の詳細情報に基づくを予測する保険業界のデータを使用します。  推奨設定が最適なチャネルと購買行動に影響するアプローチのユーザーに時刻を示すために生成されます。

**方法:**ソリューションを作成し、複数のモデルを比較します。 ソリューションでは、自動データ統合およびストアド プロシージャを使用してデータの準備も示します。 SQL Server データベース内、Azure HDInsight Spark での並列の例が提供されます。

**健康保険: 病院の維持の長さの予測**


[病院の維持の長さを予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**新機能:**注意および計画の重要な部分は、正確に予測する患者が長期的な入院を必要があります。 管理者は、どの機能が他のリソースを必要と判断する必要があるし、受ける保証患者のニーズを満たしていることができます。

**方法:**このソリューションは、データ サイエンス仮想マシンを使用して、有効になっている機械学習で SQL Server のインスタンスが含まれています。 配置済みモデルとの対話に使用できる Power BI レポートのセットも含まれています。

**顧客チャーン**


[顧客チャーン予測テンプレート (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**新機能:**データを分析して予測顧客チャーンが重要では、業界の競合するお客様の損失を管理および防止する必要があります: 銀行、通信、および製品版には、いくつかの例です。 顧客離れ分析の目標は、離れる可能性が高い顧客を特定し、そのような顧客が離れないようにして、ビジネスを維持することです。



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-whats-new-in-machine-learning-services-in-sql-serverwhat-s-new-in-sql-server-machine-learning-servicesmd"></a>12.&nbsp;[SQL Server の Machine Learning のサービスの新機能](what-s-new-in-sql-server-machine-learning-services.md)

*最終更新日: 2017-08-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_11))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 025e68a93895a3788a63847cd91bff068775acf3 6dc0be2920c670235038a126d135e08d6f16ec3a  (PR=2712  ,  Filename=what-s-new-in-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=ea75391663eb4d509c10fb785fcf321558ff0b6e) -->



> R、Python の使用を含む、マシン学習サービスは現在サポートされていません、Linux 上または Azure SQL データベース、SQL Server を実行している場合。 今後のリリースで変更を探します。
>
> ただし、予測関数を使用してネイティブ スコアリングは現在サポートされて Linux のエディションでします。

**データベース内の Python の統合**


Python ストアド プロシージャ、またはを実行する計算コンテキストとして、SQL Server コンピューターを使用してリモートで Python を実行します。 この統合表示の Python の開発者とデータ科学者、SQL Server の power を使用して、Microsoft からなどの技術革新を探索する膨大なコミュニティのための新しい手法**revoscalepy**と**microsoftml**.

SQL Server の開発者にアクセスする広範な Python ライブラリ scikit などの一般的なフレームワークを含む、オープン ソース エコシステムから-Tensorflow、Caffe および Theano/Keras を説明します。

データベースでは、機械学習; の単に Python を実行しているが、多数の他の潜在的なアプリケーションとの統合に Python SQL より高度な強力なソリューションを提供するそれぞれの言語の長所を活用することがあります。

+ **revoscalepy**

    このリリースでは最終バージョンの**revoscalepy**、ストリーミング RevoScaleR のアルゴリズムのスケーラブルな対応する Pythonic を渡しています。 線形とロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、すべて並列処理、およびリモート計算コンテキストで実行中の対応の Python モデルを作成することができます。

    詳細については、[revoscalepy--python/what-は-revoscalepy.md です) を参照してください。

+ Python のリモート計算コンテキスト

    このリリースでは、複数のデータ ソースとリモート計算コンテキストの使用をサポートします。 データ科学者や開発者は、データを参照するか、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 リモート計算コンテキストを使用する必要**revoscalepy**です。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションには、パブリック GitHub.com リポジトリ内の他のサブジェクト領域で、最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示されます: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/)です。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (3 + 12): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (5 + 0): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (5 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (19 + 82): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (1 + 8): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (12 + 1):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (0 + 1): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (7 + 1): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新しい + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (4 + 1): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)
- [新しい + 更新 (0 + 1): **Tools for SQL** docs](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新しい + 更新 (0 0 以降): **SQL のように、マスター データ サービス (MDS)** docs](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



