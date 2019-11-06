---
title: SQL Server 統合サービスの移行評価を実行する (Data Migration Assistant) |Microsoft Docs
description: Azure SQL Database または Azure SQL Database マネージインスタンスに移行する前に、Data Migration Assistant を使用してオンプレミスの SQL Server 統合サービスを評価する方法について説明します。
ms.custom: ''
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14e53b3820e784916484cbe6a15ba82cd2ed5c8e
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001374"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Data Migration Assistant を使用して SQL Server 統合サービスの移行評価を実行する

次の手順では、Data Migration Assistant を使用して、SQL Server 統合サービス (SSIS) パッケージを Azure SQL Database または Azure SQL Database マネージインスタンスに移行するための最初の評価を行う方法について説明します。

## <a name="create-an-assessment"></a>評価を作成する

1. **[新規]** (+) アイコンを選択し、 **[統合サービス]** として**評価**プロジェクトの種類を選択します。

1. ソースとターゲットのサーバーの種類を設定します。

    ソースを**SQL Server**として選択し、対象サーバーの種類を**Azure SQL Database**または**Azure SQL Database マネージインスタンス**として設定します。

1. **[作成]** をクリックします。

    ![評価の作成](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="add-sources-to-assess"></a>評価するソースの追加

1. 既定のオプションに従い、ソースの **[選択]** の横にある **[次へ]** をクリックします。

1. SQL server インスタンス名を入力し、認証の種類を選択して、適切な接続プロパティを設定します。
1. SSIS パッケージを含むフォルダーパスを入力してください
1. 該当する場合は、パッケージ暗号化パスワードを入力し、 **[接続]** をクリックします。
1. 評価するファイルシステムを選択し、 **[追加]** を選択します。
  ![ソースの追加](media/dma-assess-ssis/dma-assess-ssis-addsource.png)
1. **[ソースの追加]** を選択して接続のフライアウトメニューを開きます (複数のフォルダーを評価する必要がある場合)。
1. **[評価の開始]** をクリックします。
  ![評価の開始](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>結果の表示

互換性の問題カテゴリには、オンプレミスの SSIS パッケージを Azure SSIS Integration Runtime に移行できない部分的にサポートされている機能やサポートされていない機能があります。 その後、これらの問題に対処するための推奨事項を提供します。

![結果の表示](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>次の手順

- [SQL Server Integration Services パッケージを Azure SQL Database マネージドインスタンスに移行する](https://docs.microsoft.com/en-us/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [SQL Server Integration Services パッケージを Azure SQL Database に再展開する](https://docs.microsoft.com/en-us/azure/dms/how-to-migrate-ssis-packages)
