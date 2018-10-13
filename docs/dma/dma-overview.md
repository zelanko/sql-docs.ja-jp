---
title: Data Migration Assistant (SQL Server) の概要 |Microsoft Docs
description: Data Migration Assistant を使用して、その他の SQL Server または Azure のデータベースに SQL Server データベースを移行する方法について説明します
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, overview
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 846fbfdcfb5d99363b98bad09c6efa3a2b46b4ab
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100371"
---
# <a name="overview-of-data-migration-assistant"></a>Data Migration Assistant の概要

Data Migration Assistant (DMA) では、最新のデータ プラットフォームで、新しいバージョンの SQL Server または Azure SQL Database のデータベースの機能に影響する可能性のある互換性の問題を検出してアップグレードするが、のに役立ちます。 DMA では、パフォーマンスと信頼性の向上、ターゲット環境のことをお勧めし、移行元サーバーからターゲット サーバーに、スキーマ、データ、および非包含オブジェクトを移動することができます。

> [!NOTE] 
> (番号とデータベースのサイズ) 観点から大規模な移行をお勧めを使用すること、 [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview)、大規模なデータベースを移行することができます。
  
## <a name="capabilities"></a>Capabilities

- Azure SQL データベースへの移行、オンプレミスの SQL Server インスタンスを評価します。 評価ワークフローを使用して、Azure SQL データベースの移行に影響を及ぼすことができます、問題を解決する方法の詳細なガイダンスを提供します。 次の問題を検出するのに役立ちます。

  - 移行を妨げる問題: 互換性の問題のあるブロックを移行する、オンプレミス SQL Server データベースを Azure SQL データベースを検出します。 DMA では、これらの問題に対処するための推奨事項を提供します。

  - 部分的にサポートされているか、サポートされていない機能: 検出ソース SQL Server インスタンスで使用されている機能が部分的にサポートされているか、サポートされていません。 DMA では、包括的なは、移行プロジェクトにそれらを組み込むように Azure、および軽減の手順で使用できる別の方法の推奨事項の設定を提供します。

- オンプレミスの SQL Server へのアップグレードに影響する問題を検出します。 これらは互換性の問題として説明し、次のカテゴリに分類されます。

  - 重大な変更
  - 動作の変更
  - 非推奨の機能

- データベースがアップグレード後に活用できるターゲット SQL Server プラットフォームの新機能を検出します。 これらは、機能に関する推奨事項として説明し、次のカテゴリに分類されます。

  - パフォーマンス
  - セキュリティ
  - ストレージ

- オンプレミスの SQL Server インスタンスをオンプレミス ネットワークからアクセスできる Azure 仮想マシン (VM) またはオンプレミスでホストされている最新の SQL Server インスタンスに移行します。 Azure VM は、VPN またはその他のテクノロジを使用してアクセスできます。 移行のワークフローでは、次のコンポーネントを移行することができます。

  - データベースのスキーマ
  - データとユーザー
  - サーバー ロール
  - SQL Server と Windows のログイン

- 移行の成功後にアプリケーションは、ターゲット SQL server データベースをシームレスに接続できます。

## <a name="supported-source-and-target-versions"></a>サポートされているソースとターゲットのバージョン

DMA を使用して、SQL Server アップグレード アドバイザーの以前のバージョンに置き換えられ、ほとんどの SQL Server バージョンのアップグレードに使用する必要があります。 サポートされているソースとターゲットのバージョンに従ってください。

**ソース**
- SQL Server 2005
- SQL Server 2008:
- SQL Server 2008 R2
- SQL Server 2012 
- SQL Server 2014
- SQL Server 2016
- Windows 上の SQL Server 2017

**ターゲット**
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- Windows および Linux 上の SQL Server 2017
- Azure SQL データベース

> [!NOTE] 
> DMA では、Azure SQL Database マネージ インスタンスは現在は、ターゲットとしてサポートしません。

## <a name="installation"></a>インストール

DMA をインストールするには、ツールからの最新バージョンをダウンロード、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=53595)、し、実行、 **DataMigrationAssistant.msi**ファイル。

## <a name="see-also"></a>関連項目

[SQL Server の移行を評価します。](../dma/dma-assesssqlonprem.md)

[Data Migration Assistant: 構成の設定](../dma/dma-configurationsettings.md)

[Data Migration Assistant を使用して移行、オンプレミスの SQL Server](../dma/dma-migrateonpremsql.md)

[Data Migration Assistant: ベスト プラクティス](../dma/dma-bestpractices.md)



