---
title: "SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 08/07/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: a689293fadb1a442f94d88cc06a9e7a4ef06650f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のダウンロード

SSMS は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS には、SQL のインスタンスを構成、監視、および管理するためのツールが備わっています。 SSMS を使用して、アプリケーションで使われるデータ層コンポーネントを配置、監視、アップグレードしたり、クエリとスクリプトを作成したりすることもできます。

SQL Server Management Studio (SSMS) を使用すると、データベースとデータ ウェアハウスがローカル コンピューターやクラウドなど、どこにあっても、クエリ、設計、および管理ができます。

**SSMS は無料です。**

SSMS 17.x は、*SQL Server Management Studio* の最新世代であり、SQL Server 2017 をサポートしています。

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.2 のダウンロード](https://go.microsoft.com/fwlink/?linkid=854085)**

**[![ダウンロード](../ssdt/media/download.png) SQL Server Management Studio 17.2 アップグレード パッケージのダウンロード (17.x から 17.2 へのアップグレード)](https://go.microsoft.com/fwlink/?linkid=854087)**

SSMS 17.x のインストールでは、16.x 以前のバージョンの SSMS がアップグレードまたは置き換えられることはありません。 SSMS 17.x は以前のバージョンとは別にサイド バイ サイドでインストールするので、両方のバージョンが使用できます。
コンピューターに SSMS のサイド バイ サイドのインストールが含まれている場合は、特定のニーズに応じて適切なバージョンを起動してください。 最新バージョンには、*Microsoft SQL Server Management Studio 17* というラベルと新しいアイコンが付いています。 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> SQL Server PowerShell モジュールは、PowerShell ギャラリーで入手できる独立したインストールになりました。  詳しくは、[ダウンロードに関する説明](download-sql-server-ps-module.md)をご覧ください。

## <a name="sql-server-management-studio"></a>[SQL Server Management Studio]

**バージョン情報**

リリース番号: 17.2 このリリースのビルド番号: 14.0.17177.0

## <a name="new-in-this-release"></a>このリリースの新機能

SSMS 17.2 は SQL Server Management Studio の最新バージョンです。 SSMS の 17.x 世代は、SQL Server 2008 から SQL Server 2017 までのほぼすべての機能領域をサポートしています。 バージョン 17.x は、SQL Analysis Service PaaS もサポートしています。

バージョン 17.2 の内容:

- Multi-Factor Authentication (MFA)
  - 多要素認証を使用したユニバーサル認証 (UA with MFA) 向けの複数ユーザーの Azure AD 認証
  - 複数ユーザーの認証をサポートするため、MFA を使用したユニバーサル認証用に新しいユーザー資格情報の入力フィールドが追加されました。
- 接続ダイアログ ボックスで、次の 5 つの認証方法がサポートされるようになりました。
  - [Windows 認証]
  - SQL Server 認証 (SQL Server Authentication)
  - Active Directory - Universal with MFA のサポート
  - Active Directory - パスワード
  - Active Directory - 統合

- DacFx のデータベースの Import/Export ウィザードで、MFA を使用したユニバーサル認証が使用できるようになりました。
- API のサポートについては、「[IUniversalAuthProvider インターフェイス](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)」を参照してください。
- MFA を使用した Azure AD ユニバーサル認証で使用される ADAL マネージ ライブラリは、バージョン 3.13.9 にアップグレードされました。
- SQL Database および SQL Data Warehouse の Azure AD 管理者設定をサポートする新しい CLI インターフェイス。

 Active Directory の認証方法の詳細については、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)」と「[SQL Server Management Studio 用に Azure SQL Database の多要素認証を構成する](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)」を参照してください。

- 出力ウィンドウには、オブジェクト エクスプローラー ノードの展開時に実行されるクエリのエントリがあります。
- Azure SQL Databases のビュー デザイナーの有効化
- SSMS でのオブジェクトのスクリプト作成の既定のスクリプト作成オプションが、オブジェクト エクスプローラーから変更されました。
  - 以前は、新しいインストールには既定で、 SQL Server の最新バージョン (現時点では SQL Server 2017) を対象に生成されたスクリプトがありました。
  - SSMS 17.2 では、新しいオプション [*スクリプト設定をソースに一致させる*] が追加されました。 *True* に設定すると、生成されるスクリプトは、オブジェクトがスクリプト化されるサーバーと同じバージョン、エンジンの種類、およびエンジンのエディションを対象にします。
  - [*スクリプト設定をソースに一致させる*] の値は既定で *True* に設定されているため、SSMS の新しいインストールは、オブジェクトのスクリプト作成を常に元のサーバーと同じターゲットにすることが自動的に既定値に設定されます。
  - [*スクリプト設定をソースに一致させる*] の値を *False* に設定すると、通常のスクリプトのターゲット オプションが有効になり、従来どおりに機能します。
  - さらに、すべてのスクリプト作成オプションが、独自のセクションの [*バージョン オプション*] に移動されました。 これらは [*全般スクリプト作成オプション*] の下にはありません。

- "Restore from URL" に National Clouds のサポートが追加されました。
- QueryStoreUI レポートで、sys.query_store_runtime_stats からの追加のメトリック (RowCount、DOP、CLR Time など) がサポートされるようになりました。
- Azure SQL Database で IntelliSense がサポートされるようになりました。
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- セキュリティ: 接続ダイアログの既定値が、サーバー証明書を信頼せず、Azure SQL Database 接続の暗号化を要求することになります。
- SQL Server on Linux のサポートに関する全般的な改良点:
 - データベース メール ノードの復帰
 - パスに関連するいくつかの問題への対処
 - 利用状況モニターの安定性の向上
 - [接続プロパティ] ダイアログでの正しいプラットフォームの表示
- パフォーマンス ダッシュボード サーバー レポートを既定のレポートとして使用できるようになりました。
  - SQL Server 2008 以降のバージョンに接続できます。
  - 欠落したインデックスのサブレポートは、最も有用なインデックスを特定しやすくするため、スコアリングを使用します。
  - 履歴待機統計サブレポートで、待機の集計がカテゴリ別になりました。 アイドル状態とスリープの待機は既定で除外されます。
  - 新しい履歴ラッチ サブレポート。
- Showplan ノードの検索では、プランのプロパティを検索できます。 テーブル名などの任意の演算子プロパティを簡単に検索できます。 プランを表示しているときに、このオプションを使用するには、次の手順を実行します。
  - プランを右クリックし、コンテキスト メニューで [ノードの検索] オプションをクリックします。
  - CTRL + F キーを使用します。

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

SQL Server Management Studio 17.2:<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

SQL Server Management Studio 17.2 アップグレード パッケージ (17.x から 17.2 へのアップグレード):<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40a)

## <a name="release-notes"></a>リリース ノート

この 17.2 リリースの問題と制限事項を次に示します。

- "Active Directory - MFA を使用したユニバーサルのサポート" を使用するクエリ ウィンドウを 1 時間以上開いた後でクエリを実行しようとすると、次のようなエラーが発生する場合があります。

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of *ConnectRetryCount* to increase the number of recovery attempts.`

   クエリを再実行すると、エラーを克服して成功します。

- MFA を使用したユニバーサル認証を使用する Azure AD では、次の SSMS 機能はサポートされていません。
  - **新しいテーブル/ビュー** デザイナーが古いスタイルのログイン プロンプトを表示して、Azure AD の認証で機能しません。
  - [**上位 200 行を編集**] 機能は、Azure AD 認証をサポートしません。
  - **登録済みサーバー** コンポーネントは、Azure AD 認証をサポートしません。
  - **データベース エンジン チューニング アドバイザー**は、Azure AD 認証でサポートされていません。 ユーザーに表示されるエラー メッセージが有益ではないという既知の問題があります。*Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…* (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした…) が、正常なメッセージである *Database Engine Tuning Advisor does not support Microsoft Azure SQL Database.(DTAClient)* (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。

**AS**

- SSAS のオブジェクト エクスプローラーは、AS Azure の接続プロパティに Windows 認証のユーザー名を表示しません。
詳細については、[SSMS changelog](sql-server-management-studio-changelog-ssms.md) のページを参照してください。

## <a name="previous-releases"></a>以前のリリース

[SQL Server Management Studio の以前のリリース](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>フィードバック

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>参照

- [チュートリアル: SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio のドキュメント](sql-server-management-studio-ssms.md)
- [追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)

