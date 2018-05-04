---
title: (データ Migration Assistant) の SQL Server の移行の評価を実行して |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 42cd32f57547f811fba379caa3bef5678dc2b50b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="perform-a-sql-server-migration-assessment"></a>SQL Server の移行の評価を実行します。
次の手順では、内部設置型 SQL Server, データ Migration Assistant を使用して、Azure の仮想マシン、または Azure SQL データベースで実行されている SQL Server に移行するため、最初の評価を実行できます。

## <a name="create-an-assessment"></a>評価を作成します。

1.  選択、**新規**(+) アイコンをクリックし、**評価**プロジェクトの種類。

2.  ソースとターゲット サーバーの種類を設定します。

    最近、内部設置型 SQL Server インスタンスに、または Azure VM でホストされている SQL Server に、内部設置型 SQL Server インスタンスをアップグレードする場合に、ソースとターゲット サーバーの種類を設定**SQL Server**です。 Azure SQL Database に移行する場合は、代わりに、ターゲット サーバーの種類に設定**Azure SQL Database**です。

3.  **[作成]** をクリックします。

    ![評価を作成します。](../dma/media/NewAssessment.png)

## <a name="choose-assessment-options"></a>評価オプションを選択します。

1. 移行を計画しているターゲット SQL Server バージョンを選択します。

2. レポートの種類を選択します。

   内部設置型 SQL Server またはターゲットの Azure VM でホストされている SQL Server に移行するため、ソース SQL Server のインスタンスを評価するときは、次の評価レポートの種類のいずれかを選択できます。

    -   **互換性の問題**

    -   **新機能の推奨事項**

    ![SQL Server のターゲットの評価レポートの種類を選択します。](../dma/media/AssessmentTypes.png)

   Azure SQL Database に移行するため、ソース SQL Server のインスタンスを評価するときは、次の評価レポートの種類のいずれかを選択できます。

    -   **データベースの互換性を確認します。**

    -   **チェック機能のパリティ**

    ![SQL データベースのターゲットの評価レポートの種類を選択します。](../dma/media/AssessmentTypes_Azure.png)

## <a name="add-databases-to-assess"></a>評価にデータベースを追加します。

1.  選択**追加ソース**接続ポップアップ メニューを開きます。

2.  SQL server インスタンス名を入力、認証の種類を選択、正しい接続プロパティを設定し、選択**接続**です。

3.  データベースを選択し、評価を選択**追加**です。

    > [!NOTE] 
    > 複数のデータベースを削除するには、shift キーまたは Ctrl キーを押しながらクリックしているときに選択して**削除ソース**です。 使用して、複数の SQL Server インスタンスからデータベースを追加することも、**追加ソース**ボタンをクリックします。

4.  をクリックして**次**評価を開始します。

    ![ソースを追加し、評価の開始](../dma/media/SelectDatabase.png)

## <a name="view-results"></a>結果の表示

評価の所要時間は、追加したデータベースの数と各データベースのスキーマのサイズによって異なります。 利用できるようになったら、データベースごとに結果が表示されます。

1.  評価を完了しているデータベースを選択しを切り替える**互換性の問題**と**機能の推奨事項**スイッチャーを使用して、します。

2.  選択したターゲット SQL Server のバージョンでサポートされているすべての互換性レベルでの互換性問題の確認、**オプション**ページ。

互換性の問題を確認するには、影響を受けるオブジェクトとその下で識別されたすべての問題の詳細を分析して**まて**、**動作の変更**、および**非推奨機能**.

![評価の結果の表示](../dma/media/ReviewResults.png)

同様に、全体の機能の推奨事項を確認できます**パフォーマンス**、**ストレージ**、および**セキュリティ**領域。

インメモリ OLTP と列ストア、Stretch Database、Always Encrypted、動的データ マスクおよび透過的なデータ暗号化などの機能のさまざまな機能に関する推奨事項について説明します。

![ビューの機能に関する推奨事項](../dma/media/FeatureRecommendations.png)

Azure SQL データベース移行のブロッキング問題と機能のパリティの問題、評価を指定します。 特定のオプションを選択して、両方のカテゴリの結果を確認します。

- **SQL Server 機能パリティ**カテゴリは、推奨事項は、Azure、および問題を緩和する手順で使用可能な他の方法の包括的なセットを提供します。 移行プロジェクトでこの作業の計画に役立ちます。

  ![SQL Server 機能のパリティ情報の表示](../dma/media/SQLFeatureParity.png)

- **互換性の問題**カテゴリは、Azure SQL データベースへの内部設置型 SQL Server データベースの移行をブロックする部分的にサポートされているか、サポートされていない機能を提供します。 これらの問題に対処するための推奨事項を用意します。

  ![ビューの互換性の問題](../dma/media/CompatibilityIssues.png)

## <a name="export-results"></a>結果のエクスポート

すべてのデータベースには、評価が完了、選択**レポートをエクスポート**結果を JSON ファイルまたは CSV ファイルにエクスポートします。 都合に合わせて独自のデータを分析できます。

同時に複数の評価を実行して開くことで、評価の状態を表示できます、**すべて評価**ページ。
