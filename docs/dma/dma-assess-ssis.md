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
ms.openlocfilehash: 84b498cbaf7a2f3d1118894157c17b8270259afa
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632866"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Data Migration Assistant を使用して SQL Server 統合サービスの移行評価を実行する

次の手順では、Data Migration Assistant を使用して、SQL Server 統合サービス (SSIS) パッケージを Azure SQL Database または Azure SQL Database マネージインスタンスに移行するための最初の評価を行う方法について説明します。

## <a name="create-an-assessment"></a>評価を作成する

1. **[新規]** (+) アイコンを選択し、 **[統合サービス]** として**評価**プロジェクトの種類を選択します。

1. ソースとターゲットのサーバーの種類を設定します。

    ソースを**SQL Server**として選択し、対象サーバーの種類を**Azure SQL Database**または**Azure SQL Database マネージインスタンス**として設定します。

1. **[作成]** をクリックします。

    ![評価の作成](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="connect-to-a-server"></a>サーバーへの接続

1. 既定のオプションに従い、ソースの **[選択]** の横にある **[次へ]** をクリックします。
1. SQL server インスタンス名を入力し、認証の種類を選択して、適切な接続プロパティを設定します。
1. OptionalSSIS パッケージが格納されているフォルダーパスを入力します。
1. Optional該当する場合は、パッケージ暗号化パスワードを入力します。
1. [転送元の SQL server に**接続**する] をクリックします。
  ソース](media/dma-assess-ssis/dma-assess-ssis-addsource.png) の追加 ![

## <a name="add-sources-to-assess"></a>評価するソースの追加

1. 評価する SSIS パッケージのストレージの種類を選択し、 **[追加]** を選択します。
ソース](media/dma-assess-ssis/dma-assess-ssis-addsource-type.png) の追加 ![
1. **[ソースの追加]** を選択して接続のフライアウトメニューを開きます (複数のフォルダーを評価する必要がある場合)。
1. **[評価の開始]** をクリックします。
  ![評価の開始](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>結果の表示

互換性の問題カテゴリでは、オンプレミスの SSIS パッケージの Azure-SSIS Integration Runtime への移行をブロックする、部分的にサポートされている機能またはサポートされていない機能が提供 その後、これらの問題に対処するための推奨事項を提供します。

![結果の表示](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>次の手順

- [オンプレミスの SSIS ワークロードを ADF の SSIS に移行する方法の概要](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)
- [SQL Server Integration Services パッケージを Azure SQL Database マネージドインスタンスに移行する](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [SQL Server Integration Services パッケージを Azure SQL Database に再展開する](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages)
