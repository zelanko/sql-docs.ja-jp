---
title: Data Migration Assistant (SQL Server) の概要 |Microsoft Docs
description: Data Migration Assistant を使用して、その他の SQL Server または Azure のデータベースに SQL Server データベースを移行する方法について説明します
ms.custom: ''
ms.date: 03/12/2019
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
manager: jroth
ms.openlocfilehash: 2766005287a522a84d209d995be0de9a94e45c02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794345"
---
# <a name="overview-of-data-migration-assistant"></a>Data Migration Assistant の概要
Data Migration Assistant (DMA) によっては、新しいバージョンの SQL Server または Azure SQL Database でデータベースの機能に影響する可能性のある互換性の問題を検出することにより、最新のデータ プラットフォームにアップグレードします。 DMA では、パフォーマンスと信頼性の向上、ターゲット環境のことをお勧めし、移行元サーバーからターゲット サーバーに、スキーマ、データ、および非包含オブジェクトを移動することができます。

> [!NOTE] 
> (番号とデータベースのサイズ) 観点から大規模な移行をお勧めを使用すること、 [Azure Database Migration Service](/azure/dms/dms-overview)、大規模なデータベースを移行することができます。
  
## <a name="get-data-migration-assistant"></a>Data Migration Assistant を入手する
DMA をインストールするには、ツールからの最新バージョンをダウンロード、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=53595)、し、実行、 **DataMigrationAssistant.msi**ファイル。

## <a name="capabilities"></a>Capabilities
- Azure SQL データベースへの移行、オンプレミスの SQL Server インスタンスを評価します。 評価ワークフローを使用して、Azure SQL データベースの移行に影響を及ぼすことができます、問題を解決する方法の詳細なガイダンスを提供します。 次の問題を検出するのに役立ちます。

  - 移行を妨げる問題。 Azure SQL データベースに、オンプレミス SQL Server データベースを移行をブロックする互換性の問題を検出します。 DMA では、これらの問題に対処するための推奨事項を提供します。

  - 部分的にサポートされているか、サポートされていない機能: ソース SQL Server インスタンスで使用されている部分的にサポートされているか、サポートされていない機能を検出します。 DMA では、包括的なは、移行プロジェクトにそれらを組み込むように Azure、および軽減の手順で使用できる別の方法の推奨事項の設定を提供します。

- オンプレミスの SQL Server へのアップグレードに影響する問題を検出します。 これらは互換性の問題として説明し、次のカテゴリに分類されます。

  - 重大な変更
  - 動作の変更
  - 非推奨の機能

- データベースがアップグレード後に活用できるターゲット SQL Server プラットフォームの新機能を検出します。 これらは、機能に関する推奨事項として説明し、次のカテゴリに分類されます。

  - パフォーマンス
  - セキュリティ
  - ストレージ

- 最新 SQL Server インスタンスがホストされている、オンプレミスをしたり、オンプレミス ネットワークからアクセスできる Azure 仮想マシン (VM) 上に、オンプレミスの SQL Server インスタンスを移行します。 Azure VM は、VPN またはその他のテクノロジを使用してアクセスできます。 移行のワークフローでは、次のコンポーネントを移行することができます。

  - データベースのスキーマ
  - データとユーザー
  - サーバー ロール
  - SQL Server と Windows のログイン

- 移行の成功後にアプリケーションは、ターゲット SQL Server データベースにシームレスに接続できます。

## <a name="prerequisites"></a>前提条件
評価を実行するには SQL Server のメンバーである必要がある**sysadmin**ロール。

## <a name="supported-source-and-target-versions"></a>サポートされているソースとターゲットのバージョン
DMA を使用して、SQL Server アップグレード アドバイザーの以前のバージョンに置き換えられ、ほとんどの SQL Server バージョンのアップグレードに使用する必要があります。 サポートされているソースとターゲットのバージョンは次のとおりです。

**ソース**
- SQL Server 2005
- SQL Server 2008
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
- Azure SQL Database Managed Instance

## <a name="see-also"></a>関連項目
[SQL Server の移行を評価します。](../dma/dma-assesssqlonprem.md)     
[Data Migration Assistant:構成設定](../dma/dma-configurationsettings.md)     
[Data Migration Assistant を使用して移行、オンプレミスの SQL Server](../dma/dma-migrateonpremsql.md)     
[Data Migration Assistant:ベスト プラクティス](../dma/dma-bestpractices.md)     
