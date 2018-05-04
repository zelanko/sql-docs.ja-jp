---
title: データ Migration Assistant (SQL Server) の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2018
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
- Data Migration Assistant, overview
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: d7349e266f1d16310bf32c3b4c0307ba5c46bf27
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-data-migration-assistant"></a>Migration Assistant のデータの概要

データ移行アシスタント (DMA) では、新しいバージョンの SQL Server と Azure SQL Database でデータベースの機能に影響する互換性の問題を検出することにより、最新のデータ プラットフォームへのアップグレードを行うことができます。 DMA は、パフォーマンスと信頼性の向上を対象となる環境のことをお勧めし、スキーマ、データ、および非包含オブジェクトを移行元サーバーからターゲット サーバーに移動することができます。

> [!NOTE] 
> (番号とデータベースのサイズ) 観点から大規模な移行をお勧めを使用する、 [Azure データベースの移行サービス](https://docs.microsoft.com/en-us/azure/dms/dms-overview)スケールでデータベースを移行することができます。
  
## <a name="capabilities"></a>Capabilities

- 内部設置型 SQL Server のインスタンスが Azure SQL データベースへの移行を評価します。 評価ワークフローでは、Azure SQL データベースの移行に影響を与えることができ、問題を解決する方法の詳細なガイダンスを提供する次の問題を検出することができます。

  - ブロックの移行に関する問題: 互換性の問題のあるブロックを移行する内部設置型 SQL Server データベースを Azure SQL データベースを検出します。 DMA は、これらの問題に対処するための推奨事項を提供します。

  - 部分的にサポートされているか、サポートされていない機能: ソース SQL Server インスタンス上で使用されている部分的にサポートされているか、サポートされていない機能を検出します。 DMA は、包括的なは、移行プロジェクトに組み込むことができるように推奨事項は、Azure、および問題を緩和する手順で使用可能な他の方法の設定を提供します。

- 内部設置型 SQL Server へのアップグレードに影響する問題を検出します。 これは、ログの互換性の問題として記述され、、次のカテゴリで整理されています。

  - 重大な変更
  - 動作の変更
  - 非推奨機能

- アップグレードした後、データベースから利点を活用できるターゲット SQL Server プラットフォームの新機能を検出します。 これは、ログ機能の推奨事項として記述され、、次のカテゴリで整理されています。

  - パフォーマンス
  - セキュリティ
  - ストレージ

- 内部設置型または内部設置型ネットワークからアクセスできる Azure 仮想マシン (VM) でホストする、最新の SQL Server インスタンスに内部設置型 SQL Server インスタンスを移行します。 Azure の仮想マシンは、VPN またはその他のテクノロジを使用してアクセスできます。 移行のワークフローでは、次のコンポーネントを移行することができます。

  - データベースのスキーマ
  - データとユーザー
  - サーバー ロール
  - SQL Server と Windows ログイン

- 移行の成功後にアプリケーションは、ターゲット SQL server データベースをシームレスに接続できます。

## <a name="supported-source-and-target-versions"></a>サポートされているソースとターゲットのバージョン

DMA は、SQL Server アップグレード アドバイザーの以前のバージョンを置き換えるしのほとんどの SQL Server バージョンのアップグレードで使用する必要があります。 サポートされているソースとターゲット バージョンに従ってください。

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
- Windows と Linux 上の SQL Server 2017
- Azure SQL Database

> [!NOTE] 
> DMA はサポートされていません Azure SQL データベースのマネージ インスタンスのターゲットとして。

## <a name="installation"></a>インストール

DMA をインストールするから、ツールの最新バージョンをダウンロード、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=53595)、し、実行、 **DataMigrationAssistant.msi**ファイル。

## <a name="see-also"></a>参照

[SQL Server の移行を評価します。](../dma/dma-assesssqlonprem.md)

[データ移行のアシスタント: 構成の設定](../dma/dma-configurationsettings.md)

[データ Migration Assistant を使用して移行内部設置型 SQL サーバー](../dma/dma-migrateonpremsql.md)

[データ移行のアシスタント: ベスト プラクティス](../dma/dma-bestpractices.md)



