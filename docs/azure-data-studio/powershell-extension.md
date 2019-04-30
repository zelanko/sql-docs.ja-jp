---
title: PowerShell の拡張機能
titleSuffix: Azure Data Studio
description: インストールし、Azure Data studio、PowerShell を使用してください
ms.custom: seodec18
ms.date: 04/19/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: matthend
ms.openlocfilehash: 0ffb46d5d498ba04a6916e7e2d56ffccaaa71aef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63137173"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>Azure Data Studio 用の PowerShell エディターのサポート

この拡張機能は、豊富な PowerShell エディター サポートを提供します。 [Azure Data Studio](https://github.com/Microsoft/azuredatastudio)します。
今すぐを記述し、Azure Data Studio が提供する優れた IDE のようなインターフェイスを使用して PowerShell スクリプトをデバッグできます。

![PowerShell の拡張機能](media/powershell-extension/powershell-extension.png)


## <a name="features"></a>機能のインストール

- 構文の強調表示
- コード スニペット
- コマンドレットなどの IntelliSense
- ルール ベースの分析によって提供される[PowerShell Script Analyzer](http://github.com/PowerShell/PSScriptAnalyzer)
- コマンドレットと変数の定義へ移動します。
- コマンドレットと変数の参照を検索します。
- ドキュメントとワークスペースの記号の検出
- PowerShell コードを使用して、選択した選択範囲の実行<kbd>F8</kbd>
- 使用して、カーソルの下のシンボルのオンライン ヘルプを起動<kbd>Ctrl</kbd>+<kbd>F1</kbd>
- 基本的な対話型コンソール サポートです。


## <a name="installing-the-extension"></a>拡張機能のインストール

PowerShell の拡張機能の正式なリリースをインストールするには次の手順に従って、 [Data Studio の Azure ドキュメント](https://docs.microsoft.com/sql/azure-data-studio/extensions)します。
拡張機能 ウィンドウでは、"PowerShell"の拡張機能を検索し、インストールします。  将来の拡張機能の更新に関する自動的に通知が取得されます。

VSIX パッケージをインストールすることもできます。、[リリース ページ](https://github.com/PowerShell/vscode-powershell/releases)コマンドラインを使用してインストールします。

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>プラットフォームのサポート

- **Windows 7 10 から**Windows PowerShell v3 以降と PowerShell Core
- **Linux** PowerShell core (PowerShell でサポートされているすべてのディストリビューション)
- **macOS** PowerShell Core を使用

読み取り、 [FAQ](https://github.com/PowerShell/vscode-powershell/wiki/FAQ)一般的な質問に対する回答。

## <a name="installing-powershell-core"></a>PowerShell Core のインストール

MacOS または Linux で Azure Data Studio を実行する場合、PowerShell Core をインストールする必要もあります。

PowerShell Core はオープン ソース プロジェクト[GitHub](https://github.com/powershell/powershell)します。
MacOS または Linux のプラットフォームで PowerShell Core のインストールの詳細については、次の記事を参照してください。

- [Linux 上の PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [MacOS での PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)

## <a name="example-scripts"></a>スクリプトの例

拡張機能のいくつかの例のスクリプトがある`examples`フォルダーを編集およびデバッグ機能の PowerShell の検出に使用することができます。  チェック アウト、含まれる[README.md](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md)ファイルを使用する方法について説明します。

このフォルダーは、次のパスにあります。

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

または、拡張機能のプレビュー バージョンを使用している場合

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

ビュー/オープン、拡張機能の例では、Azure Data Studio、するには、PowerShell コマンド プロンプトから、次を実行します。

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="sql-powershell-examples"></a>SQL PowerShell の例
これらの例 (下記) を使用するためから SqlServer モジュールをインストールする必要があります、 [PowerShell ギャラリー](https://www.powershellgallery.com/packages/SqlServer)します。

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> バージョン`21.1.18102`以降、`SqlServer`モジュールは、サポート[PowerShell Core](https://github.com/PowerShell/PowerShell) 6.2 および Windows PowerShell のほかに、アップします。

この例では使用して、 `Get-SqlInstance` ServerA と ServerB の SMO Server オブジェクトを取得するコマンドレットです。  このコマンドは、インスタンス名を含める出力の既定バージョンについては、サービス パック、および CU の更新プログラムのインスタンスのレベル。

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

サンプルをどのような出力のようになります。

```
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```

次の例を実行、 `dir` (別名`Get-ChildItem`)、登録済みサーバー ファイルに表示されているすべての SQL Server インスタンスの一覧を取得し、使用して、`Get-SqlDatabase`それらのインスタンスの各データベースの一覧を取得するコマンドレット。

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

サンプルをどのような出力のようになります。

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa
master               Normal        6.00 MB  368.00 KB Simple       140 sa
model                Normal       16.00 MB    5.53 MB Full         140 sa
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa
```

この例では、 `Get-SqlDatabase` ServerB 上では、すべてのデータベースの一覧を取得するコマンドレットは、グリッドとテーブルを表示します (を使用して、`Out-GridView`コマンドレット) を選択するデータベースをバックアップする必要があります。  ユーザーが、[OK] ボタンをクリックすると、強調表示されているデータベースのみをバックアップします。

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

この例では、登録済みサーバー ファイルに表示されているすべての SQL Server インスタンスの一覧を取得しますが、呼び出し、`Get-SqlAgentJobHistory`表示されている SQL Server インスタンスごとに、午前 0 時からすべての失敗した SQL エージェント ジョブをレポートします。

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

### <a name="sql-powershell-examples"></a>SQL PowerShell の例
これらの例 (下記) を使用するためから SqlServer モジュールをインストールする必要があります、 [PowerShell ギャラリー](https://www.powershellgallery.com/packages/SqlServer)します。

```powershell
Install-Module -Name SqlServer -AllowPrerelease
```

この例では使用して、 `Get-SqlInstance` ServerA と ServerB の SMO Server オブジェクトを取得するコマンドレットです。  このコマンドは、インスタンス名を含める出力の既定バージョンについては、サービス パック、および CU の更新プログラムのインスタンスのレベル。

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

サンプルをどのような出力のようになります。

```
Instance Name             Version    ProductLevel UpdateLevel
-------------             -------    ------------ -----------
ServerA                   13.0.5233  SP2          CU4
ServerB                   14.0.3045  RTM          CU12
```

この例でを実行、 `dir` (エイリアスの`Get-ChildItem`)、登録済みサーバー ファイルに表示されているすべての SQL Server インスタンスの一覧を取得し、使用して、`Get-SqlDatabase`それらのインスタンスの各データベースの一覧を取得するコマンドレットです。

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

サンプルをどのような出力のようになります。

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level      
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa   
master               Normal        6.00 MB  368.00 KB Simple       140 sa   
model                Normal       16.00 MB    5.53 MB Full         140 sa   
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa   
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa   
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa   
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa   
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa   
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa   
```

この例では、 `Get-SqlDatabase` ServerB 上では、すべてのデータベースの一覧を取得するコマンドレットは、グリッドとテーブルを表示します (を使用して、`Out-GridView`コマンドレット) を選択するデータベースをバックアップする必要があります。  ユーザーが、[OK] ボタンをクリックすると、強調表示されているデータベースのみをバックアップします。

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

この例では、もう一度、登録済みサーバー ファイルに表示されているすべての SQL Server インスタンスの一覧取得を呼び出して、`Get-SqlAgentJobHistory`表示されている SQL Server インスタンスごとに、午前 0 時からすべての失敗した SQL エージェント ジョブをレポートします。

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

## <a name="reporting-problems"></a>問題の報告

PowerShell の拡張機能で問題が発生した場合は、次を参照してください。[トラブルシューティング docs](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)およびレポート問題の診断について。

#### <a name="security-note"></a>セキュリティに関する注意

すべてのセキュリティ問題では、次を参照してください。[ここ](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security)します。

## <a name="contributing-to-the-code"></a>コードに貢献します。

チェック アウト、[開発ドキュメント](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md)この拡張機能に投稿する方法の詳細については。

## <a name="maintainers"></a>管理者

- [Keith Hill](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- [Tyler Leonhardt](https://github.com/tylerl0706) - [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Rob Holt](https://github.com/rjmholt)

## <a name="license"></a>ライセンス

この拡張機能は[MIT license](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt)します。 このプロジェクトのリリースを含むサードパーティ製バイナリについて詳しくは、次を参照してください。、[サード パーティに関する通知](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt)ファイル。

## <a name="code-of-conductconduct-md"></a>[倫理規定][conduct-md]

このプロジェクトを採用しています、 [Microsoft オープン ソース倫理規定][conduct-code]します。
詳細については、次を参照してください。、 [FAQ の実施コード][ conduct-FAQ]にお問い合わせくださいまたは[ opencode@microsoft.com ] [ conduct-email]その他の質問またはコメントです。

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md
