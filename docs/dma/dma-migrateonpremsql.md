---
title: "内部設置型 SQL サーバー (データ Migration Assistant) の移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords: Data Migration Assistant, on-premises SQL Server
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 666236842318cfba0cee38f71ac694eef86cdbf5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="migrate-on-premises-sql-server-using-data-migration-assistant"></a>データ Migration Assistant を使用して、内部設置型 SQL サーバーの移行します。

この記事では、データ Migration Assistant を使用して SQL Server の移行の手順を説明します。

データ Migration Assistant シームレスな評価と最新、内部設置型 SQL Server と SQL Azure の仮想マシン データのプラットフォームへの移行を提供します。  

移行を実行する次のタスクを完了します。

- [新しい移行プロジェクトを作成します。](#create-a-new-migration-project)
- [ソースとターゲットを指定します。](#specify-source-and-target)
- [データベースを追加します。](#add-databases)
- [ログインを選択します。](#select-logins)

## <a name="create-a-new-migration-project"></a>新しい移行プロジェクトを作成します。

1. をクリックして**新規**(+) クリックし、左側のウィンドウで、**移行**プロジェクトの種類。

1. ソースとターゲット サーバーの種類を設定**SQL Server**を内部設置型 SQL サーバーをアップグレードする場合に、モダン内部設置型 SQL Server。

1. **[作成]**をクリックします。

   ![移行プロジェクトを作成します。](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>ソースとターゲットを指定します。

1. ソースの SQL Server インスタンス名を入力します、**サーバー名**フィールドで、**サーバーの詳細をソース**セクションです。 

1. 選択、**認証の種類**ソース SQL Server インスタンスでサポートされています。

1. ターゲットのために SQL Server インスタンス名を入力してください。、**サーバー名**フィールドで、**対象のサーバーの詳細**セクションです。 

1. 選択、**認証の種類**対象の SQL Server インスタンスでサポートされています。

1. 選択すると、接続を暗号化することをお勧め**接続を暗号化**で、**接続プロパティ**セクションです。

1. **[次へ]** をクリックします。

   ![指定ソースとターゲット ページ](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>データベースを追加します。

1. 左側のウィンドウでそれらのデータベースのみを選択して移行する特定のデータベースを選択して、**データベースを追加する**ページ。

   移行のため既定では、ソース SQL Server インスタンス上のすべてのユーザー データベースの選択します。

1. ページの右側にある移行の設定を使用すると、次の手順を実行して、データベースに適用されている移行オプションを設定できます。

   > [!NOTE]
   > 左側のウィンドウで、サーバーを選択して、移行しているすべてのデータベースには、移行の設定を適用できます。 左側のウィンドウで、データベースを選択して固有の設定で個々 のデータベースを構成することもできます。


 1. 指定して、**バックアップ操作のソースとターゲットの SQL サーバーでアクセス可能な場所を共有**です。 ソースを実行しているサービス アカウントに対する書き込み共有の場所に特権を SQL Server インスタンスと、ターゲット サービス アカウントが共有の場所に対する権限を読み取ることを確認してください。

 1. データと、対象サーバー上のトランザクションのログ ファイルを復元する場所を指定します。

    ![データベース ページを追加します。](../dma/media/AddDatabases.png)

1. ソースとターゲットの SQL Server インスタンスが、アクセス権のある共有の場所を入力、**場所のオプションを共有**ボックス。

1. 共有の場所を提供できない場合、ソースとターゲットの両方の SQL サーバーにアクセスを選択する**データベース バックアップを対象サーバーが読み取りし、からの復元を別の場所にコピー**です。 次の値を入力、**復元オプションのバックアップの場所**ボックス。 

   データ Migration Assistant を実行しているユーザー アカウントが、バックアップの場所に権限を読み取りがあるかどうかを確認し、権限をターゲット サーバーを復元元の場所に書き込めません。

   ![データベースのバックアップを別の場所にコピーするオプション](../dma/media/CopyDatabaseDifferentLocation.png)

1. **[次へ]** をクリックします。

Migration Assistant のデータの検証を行います、バックアップ フォルダーに対するデータとログ ファイルの場所。 いずれかの検証に失敗した場合を修正してください、オプションとクリック**次**です。

## <a name="select-logins"></a>ログインを選択します。

1. 移行のための特定のログインを選択します。

   > [!IMPORTANT]
   > 移行用に選択されたデータベースの 1 つまたは複数のユーザーにマップされるログインを選択してください。   

   既定では、移行対象となるすべての SQL Server と Windows ログインが移行に選択されます。

1. をクリックして**移行を開始**です。

   ![ログインを選択し、移行の開始](../dma/media/SelectLogins.png)

## <a name="view-results"></a>結果の表示

移行の進行状況を監視することができます、**結果を表示**ページ。

![ビューの結果 ページ](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>移行の結果をエクスポートします。

1. をクリックして**レポートをエクスポート**の下部にある、**結果を表示**移行の結果を CSV ファイルに保存するページ。

1. ログインの移行に関する情報の詳細については、保存済みのファイルを確認し、変更内容を確認します。

## <a name="see-also"></a>参照

[データ Migration Assistant (DMA)](../dma/dma-overview.md)

[データ移行のアシスタント: 構成の設定](../dma/dma-configurationsettings.md)

[データ移行のアシスタント: ベスト プラクティス](../dma/dma-bestpractices.md)
