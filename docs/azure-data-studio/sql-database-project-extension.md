---
title: SQL Database プロジェクトの拡張機能
description: Azure Data Studio の SQL Database プロジェクトの拡張機能 (プレビュー) をインストールして使用する
ms.custom: seodec18
ms.date: 07/30/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 39ebf2d26e69e47edc700a489743d70762bef7b0
ms.sourcegitcommit: bf5acef60627f77883249bcec4c502b0205300a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88199988"
---
# <a name="sql-database-projects-extension-preview"></a>SQL Database プロジェクトの拡張機能 (プレビュー)

SQL Database プロジェクトの拡張機能 (プレビュー) は、プロジェクトベースの開発環境で SQL データベースを開発するための拡張機能です。 この拡張機能は現在プレビュー段階であり、[Azure Data Studio Insider Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main) で使用できます。


## <a name="features"></a>特徴
1. 接続されたデータベースからプロジェクトを作成する 
2. 空のプロジェクトを新しく作成する
3. [Azure Data Studio](sql-database-project-extension-getting-started.md) または [SQL Server Data Tools](../ssdt/sql-server-data-tools.md) で以前に作成されたプロジェクトを開く 
4. プロジェクトのテーブル、ビュー、ストアド プロシージャ、またはカスタム スクリプトを追加または削除してプロジェクトを編集する 
5. フォルダー内のファイルまたはスクリプトを整理する 
6. システム データベースまたはユーザー DACPAC への参照を追加する
7. 1 つのプロジェクトをビルドする 
8. 1 つのプロジェクトをデプロイする
9. デプロイ プロファイルから接続の詳細 (SQL Windows 認証) と SQLCMD 変数を読み込む 

## <a name="install-the-sql-database-projects-extension"></a>SQL Database プロジェクトの拡張機能をインストールする

1. 拡張機能マネージャーを開いて、使用可能な拡張機能にアクセスします。  そのためには、拡張機能アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。
2. 拡張機能の検索ボックスに名前の一部または全部を入力して、"*SQL Database プロジェクト*" の拡張機能を特定します。 使用可能な拡張機能を選択すると、その詳細が表示されます。

   ![拡張機能のインストール](media/extensions/sql-database-projects-extension/install-database-projects.png)

3. 必要な拡張機能を選択して**インストール**します。
4. **[再読み込み]** を選択して拡張機能を有効にします (拡張機能を初めてインストールするときにのみ必要です)。
5. アクティビティ バーから [ファイル] アイコンを選択するか、 **[表示]** メニューから **[エクスプローラー]** を選択します。 **プロジェクト**用の新しい viewlet が使用できるようになりました。


   > [!NOTE]
   > プロジェクトのビルド機能には .NET Core SDK が必要であり、拡張機能でそれを検出できない場合は、.NET Core SDK をインストールするように求められます。  .NET Core SDK (v3.1 以降) は、[https://dotnet.microsoft.com/download/dotnet-core/3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) からダウンロードしてインストールできます。

   > [!NOTE]
   > すべての機能を使用するには、SQL Database プロジェクトの拡張機能と共に [Schema Compare の拡張機能](schema-compare-extension.md)をインストールすることをお勧めします。

## <a name="known-limitations"></a>既知の制限事項
1. Azure Data Studio viewlet でプロジェクト参照を追加したり、既存のプロジェクト参照を読み込んだりすることは、現在はサポートされていません。 
2. 現在、Azure Data Studio viewlet では、リンクとしてのファイルの読み込みはサポートされていませんが、ファイルはツリーの最上位レベルに読み込まれ、ビルドによりこれらのファイルが正常に組み込まれます。 
3. 現在、viewlet でのデプロイ前およびデプロイ後のスクリプトの追加と読み込みはサポートされていません。ただし、これらのファイルをプロジェクトに手動で追加すると、ビルド時に受け入れられます。 
3. プロジェクト内の SQLCLR オブジェクトは、.NET Core バージョンの DacFx ではサポートされていません。 
3. タスク (ビルド、発行) はユーザー定義ではありません
3. DacFx によって定義されたターゲットを発行します
3. ソース管理の統合と新しいプロジェクトの作成では、.gitignore ファイルは自動的に作成されません 
3. WSL 環境のサポートは制限されています 

## <a name="next-steps"></a>次のステップ
- [SQL Database プロジェクトの拡張機能をお使いになる前に](sql-database-project-extension-getting-started.md)
- [Azure Data Studio の SQL Database プロジェクトの拡張機能を使用してプロジェクトをビルドして発行する](sql-database-project-extension-build.md)