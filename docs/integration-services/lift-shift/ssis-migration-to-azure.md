---
title: SQL Server Integration Services の Azure への移行に関する概要 | Microsoft Docs
description: この記事では、SQL Server Integration Services を Azure に移行するためのプロセスとツールを紹介しています。
ms.date: 04/10/2020
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81fb9b9cb792cf350137a375e7a2e25643656b6e
ms.sourcegitcommit: 335d27d0493ddf4ffb770e13f8fe8802208d25ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "81002853"
---
# <a name="migrate-on-premises-ssis-workloads-to-ssis-in-adf"></a>ADF でオンプレミスの SSIS ワークロードを SSIS に移行する

この記事では、SQL Server Integration Services (SSIS) ワークロードを ADF の SSIS に移行するのに役立つプロセスとツールを一覧表示します。

[移行の概要](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)に関するページでは、オンプレミスの SSIS から ADF の SSIS への ETL ワークロードの移行プロセス全体が紹介されています。

移行プロセスは、2 つのフェーズで構成されます。[評価](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#assessment)と[移行](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration)です。

## <a name="assessment"></a>評価

Data Migration Assistant (DMA) は、この目的のために自由にダウンロード可能なツールであり、ローカルにインストールして実行できます。 種類が Integration Services の DMA 評価プロジェクトを作成して、SSIS パッケージを一括して評価し、互換性の問題を特定できます。

[Database Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview) を取得し、[パッケージの評価を実行します](https://docs.microsoft.com/sql/dma/dma-assess-ssis)。

## <a name="migration"></a>移行

ソース SSIS パッケージのストレージの種類とデータベース ワークロードの移行先によって、SSIS パッケージと SSIS パッケージ実行をスケジュールする SQL Server エージェント ジョブを移行する手順は異なる場合があります。 詳細については、 [こちらのページ](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration)をご覧ください。

## <a name="next-steps"></a>次のステップ

- 「[SSIS パッケージを Azure SQL Database マネージド インスタンスに移行する](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)」。
- [SQL Server Management Studio (SSMS) を使用して SSIS ジョブを Azure Data Factory (ADF) に移行する](https://docs.microsoft.com/azure/data-factory/how-to-migrate-ssis-job-ssms)。
