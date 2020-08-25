---
title: SQL Server インポートの拡張機能
description: .txt ファイルと .csv ファイルを SQL テーブルに変換するウィザードである、Azure Data Studio 用の SQL Server インポート拡張機能 (プレビュー) をインストールして使用する方法について説明します。
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9ecee71588cb54cb23c813cf5009b92159cf94d6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765921"
---
# <a name="sql-server-import-extension-preview"></a>SQL Server インポートの拡張機能 (プレビュー)

SQL Server インポートの拡張機能 (プレビュー) では、.txt ファイルと .csv ファイルが SQL テーブルに変換されます。 このウィザードでは、[Program Synthesis using Examples (PROSE)](https://microsoft.github.io/prose/) と呼ばれるマイクロソフト リサーチ フレームワークを利用して、最小のユーザー入力でファイルをインテリジェントに解析することができます。 これはデータ ラングリングのための強力なフレームワークであり、Microsoft Excel でフラッシュ フィルを強化するのと同じテクノロジです

この機能の SSMS バージョンの詳細については、[こちら](../relational-databases/import-export/import-flat-file-wizard.md)の記事を参照してください。


## <a name="install-the-sql-server-import-extension"></a>SQL Server インポートの拡張機能をインストールする

1. 拡張機能マネージャーを開いて、使用可能な拡張機能にアクセスするには、拡張機能アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。
2. 使用可能な拡張機能を選択すると、その詳細が表示されます。

   ![拡張機能マネージャーをインポートする](media/sql-server-import-extension/import-wizard-install.png)

1. 必要な拡張機能を選択して**インストール**します。
2. **[再読み込み]** を選択して拡張機能を有効にします (拡張機能を初めてインストールするときにのみ必要です)。

## <a name="start-import-wizard"></a>インポート ウィザードを開始する

1. SQL Server インポートを開始するには、まず [サーバー] タブでサーバーへの接続を確立します。
2. 接続を確立したら、SQL テーブルにファイルをインポートするターゲット データベースにドリルダウンします。
3. データベースを右クリックし、 **[インポート ウィザード]** をクリックします。
    ![インポート ウィザードを開く](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>ファイルのインポート
1. 右クリックしてウィザードを起動すると、サーバーとデータベースは既に自動入力されています。 アクティブな接続が他にもある場合は、ドロップダウンで選択することができます。 
    
    **[参照]** をクリックしてファイルを選択します。 ファイル名に基づくテーブル名が自動的に入力されますが、それを自分で変更することもできます。

    既定では、スキーマは dbo になりますが、これは変更することができます。 **[次へ]** をクリックして続行します。
    ![入力ファイル](media/sql-server-import-extension/import-wizard-input-file.png)
1. ウィザードでは、最初の 50 行に基づいてプレビューが生成されます。 データが正確に見えることを確認する以外に、このページに追加のアクションはありません。 **[次へ]** をクリックして続行します。
    ![インポート ウィザードを開く](media/sql-server-import-extension/import-wizard-preview-data.png)
2. このページでは、列名またはデータ型に変更を加えたり、主キーかどうか、または null を許容するかどうかを変更したりできます。 変更は必要なだけ行うことができます。 **[データのインポート]** をクリックして続行します。
    ![インポート ウィザードを開く](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. このページには、選択したアクションの概要が表示されます。 ご利用のテーブルが正常に挿入されたかどうかを確認することもできます。 

    変更が必要な場合に **[完了]、[前へ]** の順にクリックすることも、別のファイルをすばやくインポートするために **[Import new file]\(新しいファイルのインポート\)** をクリックすることもできます。
    ![インポート ウィザードを開く](media/sql-server-import-extension/import-wizard-summary.png)
1. ご利用のターゲット データベースを更新するか、テーブル名に対して SELECT クエリを実行することにより、テーブルが正常にインポートされたかどうかを確認します。

## <a name="next-steps"></a>次のステップ
- インポート ウィザードの詳細については、[こちら](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/)のブログの投稿を参照してください。
- PROSE の詳細については、[こちら](https://microsoft.github.io/prose/)のドキュメントを参照してください。