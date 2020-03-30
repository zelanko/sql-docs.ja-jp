---
title: SQL Server Integration Services DevOps 概要 | Microsoft Docs
description: SSIS DevOps ツールで SSIS CICD をビルドする方法について説明します。
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a1f903d0be82d6f5057af68dce80bda1e48238a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "78225926"
---
# <a name="sql-server-integration-services-ssis-devops-tools-preview"></a>SQL Server Integration Services (SSIS) DevOps ツール (プレビュー)

[SSIS DevOps Tools](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools) 拡張機能は **Azure DevOps** マーケットプレースで入手できます。

**Azure DevOps** 組織がない場合、まず、[Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-sign-up?view=azure-devops) に新規登録し、[次の手順](https://docs.microsoft.com/azure/devops/marketplace/overview?view=azure-devops&tabs=browser#add-an-extension)で **SSIS DevOps ツール**拡張機能を追加します。

**SSIS DevOps ツール**に **SSIS Build** タスクと **SSIS Deploy** リリース タスクが含まれています。

- **SSIS Build** タスクでは、プロジェクト デプロイ モデルまたはパッケージ デプロイ モデルで dtproj ファイルをビルドできます。

- **SSIS Deploy** タスクでは、1 つまたは複数の ispac ファイルをオンプレミスの SSIS カタログと Azure-SSIS IR にデプロイしたり、SSISDeploymentManifest ファイルとその関連ファイルをオンプレミスの Azure ファイル共有にデプロイしたりできます。

## <a name="ssis-build-task"></a>SSIS Build タスク

![ビルド タスク](media/ssis-build-task.png)

### <a name="properties"></a>Properties

#### <a name="project-path"></a>プロジェクト パス

ビルドするプロジェクト フォルダーまたはファイルのパス。 フォルダー パスが指定されている場合、SSIS Build タスクでは、このフォルダーの下にあるすべての dtproj ファイルが繰り返し検索され、すべてビルドされます。

プロジェクト パスを "*空*" にすることはできません。 **.** として設定して、 リポジトリのルート フォルダーからビルドします。

#### <a name="project-configuration"></a>プロジェクトの構成

ビルドに使用されるプロジェクト構成の名前。 指定されていない場合、各 dtproj ファイルに最初に定義されているプロジェクト構成が選択されます。

#### <a name="output-path"></a>[出力パス]

[ビルド成果物の公開タスク](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/publish-build-artifacts?view=azure-devops)によってビルド成果物として公開できるビルド結果を保存するための個別フォルダーのパス。

### <a name="limitations-and-known-issues"></a>制限事項と既知の問題

- SSIS Build タスクは Visual Studio と、ビルド エージェントで必須となる SSIS デザイナーに依存します。 そのため、パイプラインで SSIS Build タスクを実行するには、Microsoft によってホストされるエージェントに **vs2017-win2016** を選択するか、自己ホスト エージェントに Visual Studio と SSIS デザイナー (VS2017 + SSDT2017 または VS2019 + SSIS Projects 拡張機能) をインストールする必要があります。

- 面倒な設定の要らないコンポーネント (SSIS Azure Feature Pack やその他のサードパーティ コンポーネント) を利用して SSIS プロジェクトをビルドするには、パイプライン エージェントが実行されているコンピューターにそのようなコンポーネントをインストールする必要があります。  Microsoft によってホストされるエージェントの場合、[PowerShell Script タスク](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/powershell?view=azure-devops)または [Command Line Script タスク](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/command-line?view=azure-devops)を追加してコンポーネントをダウンロードし、インストールしてから SSIS Build タスクを実行できます。 次に示すのは、Azure Feature Pack をインストールするための PowerShell のサンプル スクリプトです。 

```powershell
wget -Uri https://download.microsoft.com/download/E/E/0/EE0CB6A0-4105-466D-A7CA-5E39FA9AB128/SsisAzureFeaturePack_2017_x86.msi -OutFile AFP.msi

start -Wait -FilePath msiexec -Args "/i AFP.msi /quiet /l* log.txt"

cat log.txt
```

- 保護レベルの **EncryptSensitiveWithPassword** と **EncryptAllWithPassword** は SSIS Build タスクではサポートされていません。 コードベースのいずれの SSIS プロジェクトでもこの 2 つの保護レベルが使用されていないことを確認してください。使用されている場合、SSIS Build タスクの実行中、応答が停止し、タイムアウトになります。

- **ConnectByProxy** は、最近 SSDT に追加された新しいプロパティです。 Microsoft によってホストされているエージェントにインストールされた SSDT は更新されないため、回避策としてセルフホステッド エージェントを使用してください。

## <a name="ssis-deploy-task"></a>SSIS Deploy タスク

![デプロイ タスク](media/ssis-deploy-task.png)

### <a name="properties"></a>Properties

#### <a name="source-path"></a>ソース パス

デプロイするソース ISPAC ファイルまたは SSISDeploymentManifest ファイルのパス。 このパスはフォルダー パスやファイル パスになることがあります。

#### <a name="destination-type"></a>変換先の型

デプロイ先の種類。 SSIS Deploy タスクでは現在、2 つの種類がサポートされています。

- *ファイル システム*:SSISDeploymentManifest ファイルとその関連ファイルを指定のファイル システムにデプロイします。 オンプレミスと Azure ファイル共有の両方がサポートされています。
- *SSISDB*:オンプレミスの SQL Server または Azure-SSIS Integration Runtime でホストできる指定の SSIS カタログに ISPAC ファイルをデプロイします。

#### <a name="destination-server"></a>[転送先サーバー]

宛先となる SQL サーバーの名前。 これには SQL Server、Azure SQL Database、Azure SQL Database マネージド インスタンスの名前が想定されます。 このプロパティは、宛先の種類が SSISDB の場合にのみ表示されます。

#### <a name="destination-path"></a>宛先のパス

ソース ファイルがデプロイされる宛先フォルダーのパス。 次に例を示します。

- /SSISDB/\<folderName\>
- \\\\\<machineName\>\\\<shareFolderName\>\\\<optionalSubfolderName\>

フォルダーやサブフォルダーが存在しない場合、SSIS Deploy タスクによって作成されます。

#### <a name="authentication-type"></a>認証の種類

指定の宛先サーバーにアクセスするための認証の種類。 このプロパティは、宛先の種類が SSISDB の場合にのみ表示されます。 一般的に、SSIS Deploy タスクでは次の 4 つの種類がサポートされます。

- Windows 認証
- SQL Server 認証
- Active Directory - パスワード
- Active Directory - 統合

ただし、特定の種類の認証がサポートされるかどうかは、宛先サーバーの種類やエージェントの種類に左右されます。 サポート マトリックスの詳細を一覧にしたものが下の表になります。

| |Microsoft によってホストされるエージェント|自己ホスト エージェント|
|---------|---------|---------|
|オンプレミスの SQL サーバーまたは VM |該当なし|Windows 認証|
|Azure SQL|SQL Server 認証 <br> Active Directory - パスワード|SQL Server 認証 <br> Active Directory - パスワード <br> Active Directory - 統合|

#### <a name="domain-name"></a>ドメイン名

指定のファイル システムにアクセスするためのドメイン名。 このプロパティは、宛先の種類がファイル システムの場合にのみ表示されます。
自己ホスト エージェントを実行するユーザー アカウントに指定の宛先パスの読み取り/書き込みアクセスが付与されている場合、この項目は空のまま残すことができます。

#### <a name="username"></a>ユーザー名

指定のファイル システムまたは SSISDB にアクセスするためのユーザー名。 このプロパティは宛先の種類がファイル システムの場合か、認証の種類が SQL Server 認証か "アクティブ ディレクトリ - パスワード" の場合に表示されます。
宛先の種類がファイル システムであり、自己ホスト エージェントを実行するユーザー アカウントに指定の宛先パスの読み取り/書き込みアクセスが付与されている場合、この項目は空のまま残すことができます。

#### <a name="password"></a>Password

指定のファイル システムまたは SSISDB にアクセスするためのパスワード。 このプロパティは宛先の種類がファイル システムの場合か、認証の種類が SQL Server 認証か "アクティブ ディレクトリ - パスワード" の場合に表示されます。
宛先の種類がファイル システムであり、自己ホスト エージェントを実行するユーザー アカウントに指定の宛先パスの読み取り/書き込みアクセスが付与されている場合、この項目は空のまま残すことができます。

#### <a name="overwrite-existing-projects-or-ssisdeploymentmanifest-files-of-the-same-names"></a>同じ名前の既存のプロジェクトまたは SSISDeploymentManifest ファイルを上書きする

同じ名前の既存のプロジェクトまたは SSISDeploymentManifest ファイルを上書きするかどうかを指定します。 "いいえ" の場合、SSIS Deploy では、そのようなプロジェクトまたはファイルのデプロイがスキップされます。

#### <a name="continue-deployment-when-error-occurs"></a>エラーの発生時にデプロイを続行する

エラーの発生時に残りのプロジェクトまたはファイルのデプロイを続行するかどうかを指定します。 "いいえ" の場合、エラーの発生直後に SSIS Deploy タスクが停止します。

### <a name="limitations-and-known-issues"></a>制限事項と既知の問題

SSIS Deploy タスクでは現在、次のシナリオがサポートされていません。

- SSIS カタログで環境を構成する。
- 多要素認証 (MFA) のみが許可される Azure SQL Server または Azure SQL マネージド インスタンスに ispac をデプロイする。
- MSDB または SSIS パッケージ ストアにパッケージをデプロイする。

## <a name="release-notes"></a>リリース ノート

### <a name="version-013-preview"></a>バージョン 0.1.3 プレビュー

リリース日:2020 年 1 月 19 日

- 元のファイル名が変更された場合に、ispac を展開できない問題を修正しました。

### <a name="version-012-preview"></a>バージョン 0.1.2 Preview

リリース日:2020 年 1 月 13 日

- 宛先の種類が SSISDB である場合、SSIS Deploy タスク ログにより詳細な例外情報が追加されていましす。
- SSIS Deploy タスクのプロパティ Destination パスのヘルプ テキスト内の宛先パスの例が修正されています。

### <a name="version-011-preview"></a>バージョン 0.1.1 プレビュー

リリース日:2020 年 1 月 6 日

- 最小エージェント バージョン要件の制約が追加されました。 現在、この製品の最小エージェント バージョンは 2.144.0 です。
- SSIS Deploy タスクの表示テキストの間違いがいくつか修正されました。
- エラー メッセージがいくつか改善されました。

### <a name="version-010-preview"></a>バージョン 0.1.0 プレビュー

リリース日:2019 年 12 月 5 日

SSIS DevOps ツールの初回リリース。 これはプレビュー リリースです。

## <a name="next-steps"></a>次のステップ

- [SSIS DevOps 拡張機能](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools)を入手してください
