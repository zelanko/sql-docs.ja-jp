---
title: "SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 10/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "ssms のインストール、ssms のダウンロード、最新の ssms"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- "sql management studio インストール"
- "ダウンロード sql management studio"
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: be3d22491e1cf5e6446f9ac597d613e1d203a28e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のダウンロード

SSMS は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS には、SQL のインスタンスを構成、監視、および管理するためのツールが備わっています。 SSMS を使用して、アプリケーションで使われるデータ層コンポーネントを配置、監視、アップグレードしたり、クエリとスクリプトを作成したりすることもできます。

SQL Server Management Studio (SSMS) を使用すると、データベースとデータ ウェアハウスがローカル コンピューターやクラウドなど、どこにあっても、クエリ、設計、および管理ができます。

**SSMS は無料です。**

SSMS 17.x は、*SQL Server Management Studio* の最新世代であり、SQL Server 2017 をサポートしています。

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.3 のダウンロード](https://go.microsoft.com/fwlink/?linkid=858904)**

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.3 アップグレード パッケージのダウンロード (17.x から 17.3 へのアップグレード)](https://go.microsoft.com/fwlink/?linkid=858906)**

SSMS 17.x のインストールでは、16.x 以前のバージョンの SSMS がアップグレードまたは置き換えられることはありません。 SSMS 17.x は以前のバージョンとは別にサイド バイ サイドでインストールするので、両方のバージョンが使用できます。
コンピューターに SSMS のサイド バイ サイドのインストールが含まれている場合は、特定のニーズに応じて適切なバージョンを起動してください。 最新バージョンには、*Microsoft SQL Server Management Studio 17* というラベルと新しいアイコンが付いています。 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> SQL Server PowerShell モジュールは、PowerShell ギャラリーで入手できる独立したインストールになりました。  詳しくは、[ダウンロードに関する説明](download-sql-server-ps-module.md)をご覧ください。

## <a name="sql-server-management-studio"></a>[SQL Server Management Studio]

**バージョン情報**

リリース番号: 17.3

このリリースのビルド番号: 14.0.17199.0

## <a name="new-in-this-release"></a>このリリースの新機能

SSMS 17.3 は SQL Server Management Studio の最新バージョンです。 SSMS の 17.x 世代は、SQL Server 2008 から SQL Server 2017 までのほぼすべての機能領域をサポートしています。 バージョン 17.x は、SQL Analysis Service PaaS もサポートしています。

バージョン 17.3 の内容:

- インテリジェントなフレームワークを使用して、CSV ファイルのインポート エクスペリエンスを効率化するための新しい "フラット ファイルのインポート" ウィザードが追加されました。これは最小限のユーザーの介入または特殊なドメインの知識で使用できます。 詳細については、「[Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md)」 (フラット ファイルを SQL ウィザードにインポートする) を参照してください。
- オブジェクト エクスプローラーに "XEvent プロファイラー" ノードが追加されました。 詳細については、「[SSMS XEvent プロファイラーの使用](../relational-databases/extended-events/use-the-ssms-xe-profiler.md)」を参照してください。
- パフォーマンス ダッシュボードでの待機の履歴レポートの待機のフィルター処理と分類を更新しました。
- "Predict" 関数の構文チェックを追加しました。
- 外部ライブラリ管理のクエリの構文チェックを追加しました。
- 外部ライブラリ管理の SMO サポートを追加しました。
- [登録済みサーバー] ウィンドウに [PowerShell の起動] のサポートを追加しました (新しい SQL PowerShell モジュールが必要)。
- Always On: 可用性グループに[読み取り専用ルーティングのサポート](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)を追加しました。
- [Active Directory - MFA で汎用のサポート] ログインの出力ウィンドウにトレースの詳細を送信するオプションを追加しました (既定ではオフになっているため、[ツール] > [オプション] > [Azure サービス] > [Azure クラウド] > [ADAL 出力ウィンドウのトレース レベル] の下にあるユーザー設定で有効にする必要があります)。 
- クエリ ストア: 
  - クエリ ストア UI は、QDS が何らかのデータを記録している限り、QDS がオフになっている場合でもアクセスできます。
  - クエリ ストア UI で、既存レポートのすべての待機の分類法が公開されるようになりました。 これにより、顧客が上位の待機中のクエリのシナリオのロック解除などができるようになります。
- [スクリプト パラメーター ヘッダーを含める] がオプションになりました (既定で無効になっており、[ツール] > [オプション] > [SQL Server オブジェクト エクスプローラー] > [スクリプト] > [スクリプト パラメーター ヘッダーを含める] の下のユーザー設定で有効にすることができます) - [Connect アイテム 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199)。
- "RC" ブランド化を削除しました。

変更の完全なリストについては、「[SQL Server Management Studio - Changelog (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)」を参照してください。

ユーザー データの収集については、「[SQL Server のプライバシーに関する声明](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx)」を参照してください。

## <a name="supported-sql-offerings"></a>サポートされる SQL 製品

* このバージョンの SSMS は、すべての[サポート対象バージョンである SQL Server 2008 から SQL Server 2017](https://support.microsoft.com/lifecycle?C2=1044) で動作し、Azure SQL Database および Azure SQL Data Warehouse で最新のクラウド機能と連携するための最大レベルのサポートを提供します。
* SQL Server 2000 または SQL Server 2005 に対して明示的なブロックはありませんが、一部の機能が適切に機能しない可能性があります。
* また、SSMS 17.x は、SSMS 16.x または SQL Server 2014 SSMS 以前とサイドバイサイドでインストールできます。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム
  
SSMS の今回のリリースでは、最新の Service Pack を使用した次の 64 ビット プラットフォームがサポートされます。
- Windows 10 (64 ビット)
- Windows 8.1 (64 ビット)
- Windows 8 (64 ビット)
- Windows 7 (SP1) (64 ビット)
- Windows Server 2016 *
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

\* SSMS 17.X は、Windows Server 2016 より前にリリースされた Visual Studio 2015 Isolated Shell に基づいています。 Microsoft はアプリケーションの互換性を重視しており、既にリリースされているアプリケーションが最新の Windows リリースでも引き続き動作するように努めています。 Windows Server 2016 での SSMS の実行に関する問題を最小限に抑えるには、SSMS に最新の更新プログラムをすべて適用してください。 Windows Server 2016 での SSMS で問題が発生する場合は、サポートに問い合わせてください。 サポート チームは問題が SSMS、Visual Studio、または Windows の互換性のいずれに関するものかを判別します。 そしてサポート チームは、問題をさらに調査するよう適切なチームに渡します。

## <a name="ssms-installation-tips-and-issues"></a>SSMS のインストールに関するヒントと問題

### <a name="minimize-installation-reboots"></a>インストール時の再起動を最小限に抑える

* SSMS のセットアップでインストールの最後に再起動が必要になる可能性を低くするには、次の操作を実行します。
  * 最新バージョンの Visual C++ 2013 再頒布可能パッケージを実行します。 バージョン 12.00.40649.5 (またはそれ以降) が必要です。 必要なのは x64 バージョンのみです。
  * コンピューターの .NET Framework のバージョンが 4.6.1 (またはそれ以降) であることを確認します。
  * コンピューターで Visual Studio のインスタンスが他に開かれている場合はすべて閉じます。
  * OS の最新の更新プログラムがすべてコンピューターにインストールされていることを確認します。
  * これらの操作は通常、1 回だけ必要です。 SSMS の同じメジャー バージョンに対する追加アップグレードの間に、再起動が必要になる場合があります。 マイナー アップグレードでは、SSMS のすべての前提条件は既にコンピューターにインストールされています。

* 既知の問題と回避策の一覧については、「[SQL Server Management Studio - リリース ノート](../ssms/sql-server-management-studio-release-notes.md)」をご覧ください。

## <a name="available-languages"></a>使用できる言語

> [!NOTE]
> SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。

SSMS の今回のリリースは、次の言語でインストールできます。

SQL Server Management Studio 17.3:<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)

SQL Server Management Studio 17.3 アップグレード パッケージ (17.x から 17.3 へのアップグレード):<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40a)

## <a name="release-notes"></a>リリース ノート

この 17.3 リリースの問題と制限事項を次に示します。

**SSMS 全般**

- MFA を使用した UA を使用する Azure AD 認証では、次の SSMS 機能はサポートされていません。
   - データベース エンジン チューニング アドバイザーは Azure AD の認証ではサポートされていません。ユーザーに表示されるエラー メッセージが少し曖昧だという既知の問題があります。"Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…" (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした…) が、正常なメッセージである "Database Engine Tuning Advisor does not support Microsoft Azure SQL Database. (DTAClient) (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。
- DTA でクエリを分析しようとすると、次のエラーが発生します。"Object must implement IConvertible. (mscorlib)" (オブジェクトで IConvertible を実装する必要があります (mscorlib))。
- *[低下したクエリ]* がオブジェクト エクスプローラーのレポートのクエリ ストアのリストにありません。
   - 回避策: **[クエリ ストア]** ノードを右クリックし、**[View Regressed Queries]\(低下したクエリを表示します\)** を選択します。

**Integration Services (IS)**

- [catalog].[event_messagea] の [Execution_path] は、Scale Out でのパッケージの実行には正しくありません。[execution_path] は、パッケージの実行可能ファイルのオブジェクト名ではなく、"\Package" で開始します。 SSMS でパッケージ実行の概要レポートを表示すると、実行の概要の "実行パス" のリンクが機能しません。 回避策として、概要レポートの [メッセージの表示] をクリックして、すべてのイベント メッセージを確認します。



## <a name="previous-releases"></a>以前のリリース

[SQL Server Management Studio の以前のリリース](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>フィードバック

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>参照

- [チュートリアル: SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio のドキュメント](sql-server-management-studio-ssms.md)
- [追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)

