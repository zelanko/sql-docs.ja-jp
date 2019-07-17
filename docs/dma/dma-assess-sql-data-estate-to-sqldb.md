---
title: Azure SQL Database に移行する SQL Server のデータ資産のレディネスを評価 |Microsoft Docs
description: Data Migration Assistant を使用して Azure SQL Database への移行 SQL Server のデータ資産を移行する方法について説明します
ms.custom: ''
ms.date: 07/16/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: d317fb3f0c2227744318eeaead71514095afbdec
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269384"
---
# <a name="assess-the-readiness-of-a-sql-server-data-estate-migrating-to-azure-sql-database-using-the-data-migration-assistant"></a>Data Migration Assistant を使用して Azure SQL Database に移行する SQL Server のデータ資産のレディネスを評価します。

SQL Server インスタンスの移行数百や数千のデータベースを Azure SQL Database、提供、サービス (PaaS) としてのプラットフォームには、非常に長いタスクです。 可能な限りのプロセスを効率化するには、移行の準備が整っている相対について確信を持てる必要があります。 サーバー、データベースが完全にできているか、移行の準備に最小限の労力を必要とするなど、簡単に達成を識別するを容易にし、作業を迅速化します。

この記事を利用するための手順について説明します、 [Data Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview?view=sql-server-2017)適合性の結果をまとめの外部に公開する、 [Azure Migrate](https://portal.azure.com/?feature.customPortal=false#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)ハブ。

## <a name="create-a-project-and-add-a-tool"></a>プロジェクトを作成し、ツールの追加

Azure のサブスクリプションで新しい Azure Migrate プロジェクトを設定して、ツールを追加します。

Azure Migrate プロジェクトを使用して、検出、評価、および評価する場合や移行環境から収集された移行メタデータを格納します。 検出された資産を追跡し、評価と移行を調整することもプロジェクトを使用します。

1. Azure portal にサインイン**すべてのサービス**、し、Azure Migrate を検索します。
2. **サービス**、 **Azure Migrate**します。

   ![Azure Migrate - サービスを選択します](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-services.png)

3. **概要**] ページで、[**評価し、データベースを移行**します。

   ![Azure Migrate の評価の開始](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

4. **データベース** **Getting started**を選択します**ツールを追加**します。

   ![Azure Migrate は、ツールの追加](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tools.png)

5. **移行プロジェクト** タブで、(リソース グループで、1 つの作成がまだしていない) 場合は、Azure サブスクリプションとリソース グループを選択します。
6. **Project Details**プロジェクト名とプロジェクトを作成する地理的な場所を指定します。

    ![Azure Migrate - ツール ダイアログ ボックスを追加](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-add-tool-dialog.png)

    これらの地域のいずれかで Azure Migrate プロジェクトを作成することができます。

    | **Geography**  | **記憶域の場所のリージョン** |
    | ------------- | ------------- |
    | アジア | 東南アジアや東アジア |
    | Europe | 南ヨーロッパや西ヨーロッパ |
    | イギリス | 英国南部または英国西部 |
    | 米国 | 米国中西部または米国西部 2 |

    プロジェクトの指定した geography は、オンプレミスの Vm から収集されたメタデータを格納するのみ使用されます。 実際の移行のターゲット リージョンを選択できます。

7. 選択**次**、し、評価ツールを追加します。

   > [!NOTE]
   > プロジェクトを作成するときに、少なくとも 1 つの評価または移行ツールを追加する必要があります。

8. **選択評価ツール** タブで、 **Azure Migrate:データベースの評価**を追加する評価ツールとして表示されます。 評価ツールを必要がある場合は、選択、**ここでは、評価ツールを追加する Skip**チェック ボックスをオンします。 **[次へ]** を選択します。

    ![Azure Migrate - ツールの [評価] タブ](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-assessment-tool.png)

9. **選択移行ツール** タブで、 **Azure Migrate:Database Migration**を追加する移行ツールとして表示されます。 移行ツールを必要がある場合は、選択、**移行ツールを追加する、ここではスキップ**します。 **[次へ]** を選択します。

    ![Azure Migrate の選択の移行ツール タブ](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-select-migration-tool.png)

10. **確認 + ツールの追加**、設定、および選択を確認して**ツールを追加する**します。

    ![Azure Migrate - レビュー + ツール タブの追加](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-tools.png)

    プロジェクトを作成した後は、追加のツールを評価し、サーバーとワークロード、データベース、および web アプリの移行を選択できます。

## <a name="assess-and-upload-assessment-results"></a>評価し、評価結果をアップロード

作成した後、移行プロジェクト **評価ツール**の**Azure Migrate:データベースの評価**ボックスの のダウンロードとツールの Data Migration Assistant の表示を使用します。

   ![Azure Migrate の評価ツールの追加](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessment-tool-added.png)

1. Data Migration Assistant の提供、リンクを使用してダウンロードし、ソース SQL Server インスタンスへのアクセスを使用しているコンピューターにインストールします。
2. Data Migration Assistant を起動します。

### <a name="create-an-assessment"></a>評価を作成します。

1. 左側で、選択、 **+** アイコン、および選択し、評価**プロジェクトの種類**
2. プロジェクトの名前を指定し、移行元サーバーとターゲット サーバーの種類を選択します。

    以降のバージョンの SQL Server または Azure VM でホストされている SQL Server-オンプレミスの SQL Server インスタンスをアップグレードしている場合は、ソースとターゲット サーバーの種類を設定**SQL Server**します。 ターゲット サーバーの種類を設定**Azure SQL Database マネージ インスタンス**Azure SQL Database (PaaS) ターゲットの準備状態評価用です。

3. **[作成]** を選択します。

   ![Azure Migrate の Data Migration Assistant のインターフェイス](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-interface.png)

### <a name="choose-assessment-options"></a>評価オプションを選択します。

1. レポートの種類を選択します。

    次のレポートの種類の一方または両方を選択できます。
    * データベースの互換性を確認してください。
    * 機能パリティを確認してください。

   ![Azure Migrate - Data Migration Assistant - 評価オプション画面](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-options-screen.png)

2. **[次へ]** を選択します。

### <a name="add-databases-to-assess"></a>評価するためのデータベースを追加します。

1. 選択**ソースの追加**接続のポップアップ メニューを開きます。
2. SQL server インスタンス名を入力、認証の種類を選択、適切な接続のプロパティを設定および選択し、 **Connect**します。
3. データベースを選択し、評価、選択**追加**します。

   > [!NOTE]
   > 複数のデータベースを削除するには、shift キーまたは Ctrl キーを押しながらクリックし、ソースの削除中に選択することで。 ソースの追加 ボタンを使用して、複数の SQL Server インスタンスからデータベースを追加することもできます。

4. 選択**次**評価を開始します。

   ![Azure の移行 - Data Migration Assistant - ソース選択画面](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-select-sources-screen.png)

5. 評価が完了すると、選択**Azure Migrate にアップロード**します。

   ![Azure Migrate - Data Migration Assistant - 確認結果 画面](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-dma-review-results-screen.png)

6. Azure portal にサインインします。

   ![Azure Migrate - Data Migration Assistant - 確認結果 画面](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-signin.png)

7. 評価の結果をアップロードし、選択するサブスクリプションと Azure Migrate プロジェクトを選択します。**アップロード**します。

   評価のアップロードの確認を待ちます。

## <a name="view-target-readiness-assessment-results"></a>ターゲットの準備の評価結果を表示

1. Azure portal にサインイン、Azure migrate を検索し、 **Azure Migrate**します。

   ![Azure の移行 - Azure portal - サービスの検索](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-portal-search.png)

2. 選択**評価し、データベースを移行**評価の結果を取得します。

   ![Azure Migrate の評価結果の確認](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-hub-assess.png)

    SQL Server の準備の概要を表示、使用がさまざまな移行プロジェクトを選択するオプションを変更する場合を適切な移行プロジェクトを使用しているかどうかを確認できます。

    プロジェクトに移行するのには、Azure 評価の結果を更新するたびに、Azure migrate ハブすべての結果を統合し、概要レポートを提供します。  Data Migration Assistant のいくつかの評価を並列に実行し、結果を統合の対応状況レポートを取得する 1 つの移行プロジェクトにアップロードできます。

   ![Azure 移行の適合性の結果を確認してください。](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-review-readiness.png)

    **データベース インスタンスを評価**:これまでに評価される SQL Server インスタンスの数。
    **データベースを評価**:評価評価 1 つまたは複数の SQL Server インスタンス間でデータベースの合計数**SQL DB のデータベースを準備する**:Azure SQL Database (PaaS) に移行する準備がデータベースの数。
    **データベースは、Azure SQL VM の準備が完了**:データベースの数では、SQL Server Vm を Azure に移行する準備が Azure SQL Database (PaaS) に 1 つまたは複数の移行ブロックで構成されます。

3. 選択**データベース インスタンスを評価**を SQL Server インスタンス レベルのビューを取得します。

   ![Azure Migrate のレビューのインスタンスの準備](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-instances.png)

    Azure SQL Database (PaaS) に移行する各 SQL Server インスタンスの割合の準備状況を見つけることができます。

4. データベースの対応性ビューを取得する特定のインスタンスを選択します。

   ![Azure Migrate - データベースの準備状態を確認してください。](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-assessed-databases.png)

    各データベースでは、上記のビュー内の各データベースあたりの推奨されるターゲットごとの移行ブロック数を確認できます。

5. 移行ブロックの周囲の詳細を取得する DMA の評価結果を確認します。

   ![Azure Migrate の移行ブロックの確認](../dma/media//dma-assess-sql-data-estate-to-sqldb/dms-azure-migrate-migration-blockers.png)

## <a name="see-also"></a>関連項目

* [Data Migration Assistant (DMA)](../dma/dma-overview.md)
* [Data Migration Assistant:構成設定](../dma/dma-configurationsettings.md)
* [Data Migration Assistant:ベスト プラクティス](../dma/dma-bestpractices.md)
