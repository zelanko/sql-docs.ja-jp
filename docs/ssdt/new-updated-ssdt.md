---
title: "更新済み - SQL Server 用 SSDT のドキュメント | Microsoft Docs"
description: "Microsoft SQL Server 用 SQL Server Data Tools (SSDT) の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。"
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
ms.date: 06/30/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 5e43cb76dac922b3c43318b2a9f539ab19ec7bfe
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
<a id="new-and-recently-updated-sql-server-data-tools-ssdt" class="xliff"></a>

# 新規および最近の更新: SQL Server Data Tools (SSDT)



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 17 日**&nbsp; から &nbsp;**2017 年 6 月 30 日**
- *対象領域:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

<a id="new-articles-created-recently" class="xliff"></a>

## 最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


*今回は新しい記事はありません。*



&nbsp;

<a id="updated-articles-with-excerpts" class="xliff"></a>

## 更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

<a id="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd" class="xliff"></a>

### 1.&nbsp; [SQL Server Data Tools (SSDT) の変更ログ](changelog-for-sql-server-data-tools-ssdt.md)

*更新日: 2017 年 5 月 19 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 21.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cf17883ce0daf75fdf88881171bf4042558b1cf4 536fe0fe41b023a4186f494a509fa14fcbafccf4  (PR=1777  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



新機能および変更点の詳細については、[SSDT チーム ブログ](https://blogs.msdn.microsoft.com/ssdt/)を参照してください。

**SSDT 17.1**

ビルド番号: 14.0.61705.170

**新機能**

**AS プロジェクト:**
- ユーザーが 1400 モデルの UI 内の列でのヒントのエンコーディングを設定することができます。
- IntelliSense の関連モデル以外はオフライン モードで使用できるようになりました
- 表形式モデル エクスプ ローラーにモデル (1400 compat レベル テーブル モデル) 全体にわたって利用可能な名前付きの M 式を表すノードが含まれています
- Azure Active Directory ユーザー選択ウィンドウ テーブル モデルでロールのメンバーを設定するときに今すぐ使用できる Microsoft Azure ポータルの IAM に似ています

**データベース プロジェクト:**
- DacFx 17.1 に更新

**バグの修正**

- ここで、ビジネス インテリジェンス デザイナー グループ名が正しく表示されない VS2017 Visual Studio オプションで問題を修正しました
- ここでレポート プロジェクトとソリューションのコード マップを生成する、クラッシュが発生する可能性がありますまたはプロジェクトとして問題を修正しました
- Analysis Services 1400 compat レベル テーブル モデルの統合を PowerQuery をいくつかの問題を修正しました。
- ツール ウィンドウで、代入演算子できませんでした行ごとにメジャーを定義するときに、新しい DAX エディターで問題を修正しました
- パースペクティブ内のメジャーの名前を変更する場合、更新から表形式のメジャーの表示を妨げる問題を修正しました
- 更新された Analysis Services の統合ワークスペース エンジンと表形式のオブジェクト モデル 1200 の表形式プロジェクトに失敗する翻訳が含まれる原因となったバグ再発を修正する SQL Server 2016 Analysis Services サーバーに配置します。
- 新しい 1400 表形式のデータ ソースを非常に低速の creation\deletion したパフォーマンス問題を修正しました
- 別の Dsv の間ですばやくビューを変更する場合に、多次元モデルでの DSV ダイアグラムでレンダリングに停止でした問題を修正しました

**DacFx 17.1**

- その他の id 列を持つメモリ最適化テーブルで列を暗号化するときに、問題を修正しました
- データベースの作成に CATALOG_COLLATION オプションを指定 SQLDOM のサポート





&nbsp;

<a name="compactupdatedlist"/>

<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

## 最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、前のセクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [SQL Server Data Tools (SSDT) の変更ログ](#TitleNum_1)




<a name="sisters2"/>

&nbsp;

<a id="sister-articles" class="xliff"></a>

## 関連記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170630-1150  -->

<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (12 + 2): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (3 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (1 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (2 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (5 + 5): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 4): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


