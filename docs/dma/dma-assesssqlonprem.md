---
title: (Data Migration Assistant) SQL Server の移行評価の実行 |Microsoft Docs
description: Data Migration Assistant を使用して、別の SQL Server または Azure SQL Database に移行する前に、オンプレミスの SQL Server を評価する方法について説明します
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: 575645d78e7046e607b891f0a6eadd6d9395a9a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794422"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Data Migration Assistant で移行評価を SQL Server を実行します。

次の手順では、オンプレミスの SQL Server、Data Migration Assistant を使用して、Azure VM、または Azure SQL Database で実行される SQL Server に移行するため、最初の評価を実行できます。

## <a name="create-an-assessment"></a>評価を作成します。

1.  選択、**新規**(+) アイコンをクリックして、**評価**プロジェクトの種類。

2.  ソースとターゲット サーバーの種類を設定します。

    アップグレードする場合、オンプレミスの SQL Server インスタンスをオンプレミスで最新の SQL Server インスタンスまたは Azure VM でホストされている SQL Server、ソースとターゲット サーバーの種類を設定**SQL Server**します。 Azure SQL Database に移行する場合、ターゲット サーバーの種類を設定代わりに**Azure SQL Database**します。

3.  **[作成]** をクリックします。

    ![評価を作成します。](../dma/media/NewAssessment.png)

## <a name="choose-assessment-options"></a>評価オプションを選択します。

1. 移行を計画しているターゲット SQL Server バージョンを選択します。

2. レポートの種類を選択します。

   ターゲットの Azure VM でホストされている SQL Server にオンプレミスの SQL Server に移行するため、ソース SQL Server のインスタンスを評価している、ときに、次の評価レポート タイプの一方または両方を選択できます。

    -   **互換性の問題**
    -   **新機能のお勧め**

    ![SQL Server のターゲットの評価レポートの種類を選択します。](../dma/media/AssessmentTypes.png)

   Azure SQL Database に移行するため、ソース SQL Server のインスタンスを評価するときは、次の評価レポート タイプの一方または両方を選択できます。

    -   **データベースの互換性を確認してください。**
    -   **機能パリティを確認してください。**

    ![SQL Database のターゲットの評価レポートの種類を選択します。](../dma/media/AssessmentTypes_Azure.png)

## <a name="add-databases-to-assess"></a>評価するためのデータベースを追加します。

1.  選択**ソースの追加**接続フライアウト メニューを開きます。

2.  SQL server インスタンス名を入力、認証の種類を選択、適切な接続のプロパティを設定および選択し、 **Connect**します。

3.  データベースを選択し、評価、選択**追加**します。

    > [!NOTE] 
    > 複数のデータベースを削除するには、shift キーまたは Ctrl キーを押しながらクリックしているときに選択して**削除ソース**します。 使用して、複数の SQL Server インスタンスからデータベースを追加することも、**ソースの追加**ボタンをクリックします。

4.  クリックして**次**評価を開始します。

    ![ソースを追加し、評価を開始](../dma/media/SelectDatabase.png)

## <a name="view-results"></a>結果を表示します。

評価の実行時間は、追加したデータベースの数と各データベースのスキーマのサイズによって異なります。 利用可能になるとすぐに、データベースごとに結果が表示されます。

1.  評価が完了したデータベースを選択し、切り替える**互換性の問題**と**機能に関する推奨事項**スイッチャーを使用しています。

2.  選択したターゲット SQL Server のバージョンでサポートされているすべての互換性レベルで互換性の問題を確認して、**オプション**ページ。

互換性の問題を確認するには影響を受けるオブジェクト、その詳細、および可能性のある下検知したすべての問題の修正プログラムを分析することで**まて**、**動作の変更**、および**非推奨の機能**します。

![評価結果を表示します。](../dma/media/ReviewResults.png)

同様に、全体の機能の推奨事項を確認できます**パフォーマンス**、**ストレージ**、および**セキュリティ**領域。

機能に関する推奨事項では、さまざまなインメモリ OLTP で、列ストア、Stretch Database、Always Encrypted、動的データ マスク、および Transparent Data Encryption などの機能について説明します。

![機能の推奨事項の表示](../dma/media/FeatureRecommendations.png)

Azure SQL database では、評価は、移行を妨げる問題と機能パリティに関する問題を提供します。 特定のオプションを選択して、両方のカテゴリの結果を確認します。

- **SQL Server 機能パリティ**カテゴリは、Azure と軽減の手順で使用できる別の方法の推奨事項の包括的なセットを提供します。 移行プロジェクトでこの作業を計画できます。

  ![SQL Server 機能パリティ情報の表示](../dma/media/SQLFeatureParity.png)

- **互換性の問題**カテゴリには、Azure SQL データベースへのオンプレミス SQL Server データベースの移行をブロックする機能が部分的にサポートされているか、サポートされていません。 それらの問題に対処するための推奨事項を提供します。

  ![ビューの互換性の問題](../dma/media/CompatibilityIssues.png)

## <a name="export-results"></a>結果をエクスポートします。

すべてのデータベースには、評価が完了、選択**レポートをエクスポート**結果を JSON ファイルまたは CSV ファイルにエクスポートします。 都合に合わせて独自のデータを分析できます。

同時に複数の評価を実行して、評価の状態を表示するには、開く、**の評価すべて**ページ。
