---
title: SQL Operations Studio プレビューの FAQ |Microsoft ドキュメント
description: よく寄せられる質問 (FAQ) for SQL Operations Studio (プレビュー) です。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2410938dbe57dc5bcb8032cb85daf6fb12bf1a1f
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235686"
---
# <a name="includename-sosincludesname-sosmd-faq"></a>[!INCLUDE[name-sos](../includes/name-sos.md)] FAQ

## <a name="what-is-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)]とは何ですか?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] はデスクトップで動作し、Windows、macOS、および Linux で利用できるフリーで軽量なデータベース開発および運用ツールです。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] はオンプレミスまたはあらゆるクラウドで動作する Azure SQL Database、Azure SQL Data Warehouse、および SQL Server のサポートが組み込まれています。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]はお気に入りのオペレーティング システムの任意のデータベースの間で一貫した使用環境を提供します。

## <a name="where-can-i-get-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)]はどこで入手できますか？

Windows、macOS、および Linux 用の [!INCLUDE[name-sos](../includes/name-sos-short.md)] は [http://aka.ms/sqlopsstudio](download.md) からダウンロードできます。

## <a name="how-much-does-includename-sosincludesname-sos-shortmd-cost"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] の料金はどれくらいですか?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] の個人利用、または商用目的の利用は無料です。

## <a name="who-should-use-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] は誰が使用すべきですか?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は誰でも使用できます。ただし、データベース開発者、データベース管理者、システム管理者、および独立系ソフトウェア ベンダーによって実行されるタスクを簡略化するために設計されています。


## <a name="what-can-i-do-with-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] で何ができますか?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は、Visual Studio Code の上に構築されており、SQL を操作する際、キーボードベースの近代的なコード ワークフロー体験を提供します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] シンプルで複数のタブ ウィンドウ、豊富な SQL エディター、IntelliSense、キーワードの入力候補、コード スニペット & コード ナビゲーションおよびソース管理の統合 (Git および TFS) などの組み込みの機能を持つ簡単な 1 日に依存するコア エクスペリエンスを使用します。 オンデマンド クエリを実行、表示 (&) text、JSON、または Excel として結果を保存、データを編集、整理 (&)、お気に入りのデータベース接続を管理して閲覧できる使い慣れたオブジェクト内のデータベース オブジェクトを参照します。

お気に入りのコマンド ライン ツールを使用して (PowerShell、sqlcmd、bcp、psql、たとえば、Bash と ssh) 内で右統合ターミナル ウィンドウで、[!INCLUDE[name-sos](../includes/name-sos-short.md)]ユーザー インターフェイス。 簡単に生成し、作成を実行し、開発またはテスト目的で、データベースのコピーを作成するデータベース オブジェクトのスクリプトを挿入します。 により、生産性、スマート コード スニペットと豊富なグラフィカルなエクスペリエンスを新しいデータベースやデータベース オブジェクト (テーブル、ビュー、ストアド プロシージャ、ユーザー、ログイン、ロールなど) などを作成または既存のデータベース オブジェクトを更新します。 使用する豊富なカスタマイズ可能なダッシュ ボードの監視し、データベース内部設置型で、Azure またはクラウドでのパフォーマンスのボトルネックをすばやくトラブルシューティングします。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は、データベースをバックアップして復元するための一貫した使用環境を提供します。SQL Server Always On 可用性グループの計画的なサポートにより、ミッション クリティカルな SQL Server データベースの可用性グループを簡単に構成、監視、トラブルシューティングし、障害時にセカンダリ データベースにすばやくフェールオーバーできます。
[!INCLUDE[name-sos](../includes/name-sos-short.md)] 生産性を高める DevOps のライフ サイクルの任意のオペレーティング システムで任意のデータベース内に設計されています。 その結果を常に、コントロールとリスクを減らすより速く、問題を解決および継続的に顧客の期待を超える値を提供します。


## <a name="is-includename-sosincludesname-sos-shortmd-open-source"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] はオープンソースですか?

[!INCLUDE[name-sos](../includes/name-sos-short.md)] のソース コードと、データ プロバイダーは GitHub で利用可能です。(Visual Studio Code に基づいた) [!INCLUDE[name-sos](../includes/name-sos-short.md)] のフロントエンドのソース コードは、ソフトウェアを変更して使用するための権利を提供するソース コード EULA の下で使用できますが、再配布したりクラウド サービスでホストしたりすることはできません。

## <a name="do-you-plan-to-open-source-ssms"></a>SSMSをオープンソースにする計画はありますか？

いいえ。 ただし、次世代のマルチOS CLIおよびGUIツールはオープンソースです。 たとえば、VS Code、mssql scripter、およびmsql CLIのmssql拡張は、すべてGitHub上のオープンソースです。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]のソースコードはGitHubで利用可能です。


## <a name="now-that-there-is-includename-sosincludesname-sos-shortmd-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)]が提供されることによって、Microsoft は SSMS と SSDT を廃止する予定ですか?

いいえ。 次世代のマルチOSおよびマルチDB CLIおよびGUIツールに加えて、主要なWindowsツール（SSMS、SSDT、PowerShell）への投資も継続されます。 目標は、お客様が選択したプラットフォーム上でお客様が望むツールをシナリオに使用するかどうかを選択できるようにすることです。


## <a name="includename-sosincludesname-sos-shortmd-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] に SSMS/SSDT の機能がありません。追加されますか?
シナリオと顧客またはビジネスのニーズによって異なります。優先順位の参考のために、[GitHub](https://github.com/microsoft/sqlopsstudio/issues) で提案してください。


## <a name="i-understand-includename-sosincludesname-sos-shortmd-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>理解しました[!INCLUDE[name-sos](../includes/name-sos-short.md)]mssql VS Code 拡張機能は、新しいで電源を切断*ツールのサービス*内部的 SMO Api を使用します。 SMO は、Linux と macOS で使用可能ですか。

SMO Api まだご利用いただけません Linux または macOS で利用できるようにします。 必要な .NET Core に SMO Api のサブセットを移植お[!INCLUDE[name-sos](../includes/name-sos-short.md)]ロードマップの一環として展開する予定があるとします。
GitHub では、SQL ツールのサービス: [ https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice)です。


## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>DACFx Api や sqlpackage.exe や Linux や macOS を SSDT に移植する予定ですか。

長期的なロードマップ上にあります。 優先順位の参考のために、[GitHub](https://github.com/microsoft/sqlopsstudio/issues) で提案してください。


## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>SQL PowerShell コマンドレットで利用できる Linux や macOS しますか。

SQL PowerShell は、現在 PowerShell ギャラリーで入手でき、Linux 上の SQL を含む任意の場所で実行されている SQL Server で作業するために Windows で使用できます。Linux および macOS への SQL PowerShell コマンドレットの提供はロードマップに含まれます。優先順位の参考のために、[GitHub](https://github.com/microsoft/sqlopsstudio/issues) で提案してください。

