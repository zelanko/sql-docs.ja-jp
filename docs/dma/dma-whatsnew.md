---
title: Data Migration Assistant (SQL Server) の新 |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 31c75b46eb01e5d892a7930ab0bec84b19e02a54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655660"
---
# <a name="whats-new-in-data-migration-assistant"></a>Data Migration Assistant の新機能
この記事では、各リリースで追加の Data Migration Assistant (DMA) を示します。

## <a name="dma-v40"></a>DMA v4.0
DMA の v4.0 のリリースでは、データベースをホストしているコンピューターから収集されたパフォーマンス カウンターに基づいて、Azure SQL データベース SKU の推奨最小値を識別するためにユーザーが Azure SQL データベースの SKU の推奨事項機能について説明します。 この機能は、1 か月あたりの推定コストに加え、レベル、コンピューティング レベル、および最大データ サイズ、価格に関連する推奨事項を提供します。 一括で Azure にすべてのデータベースをプロビジョニングする機能も提供します。

> [!NOTE]
> この機能をコマンド ライン インターフェイス (CLI) でのみ利用可能には、現在はあります。 DMA のユーザー インターフェイスを使用してこの機能のサポートは、今年の後半の配信予定です。

追加の詳細は、記事を参照してください。[オンプレミス データベースの適切な Azure SQL データベース SKU を特定](dma-sku-recommend-sql-db.md)します。

## <a name="dma-v36"></a>DMA v3.6
DMA の v3.6 のリリースでは、最も一般的な移行ブロックによって影響を受けるスキーマ オブジェクトの「自動修正」について説明します。

このリリースでは、次の移行ブロックの自動修正を提供し、動作が問題を変更します。
- 非修飾結合の構文を使用するスキーマ オブジェクト。
- レガシ RAISEERROR ステートメントを使用して、スキーマ オブジェクト。
- 整数リテラルで順序を使用する SQL ステートメント。

DMA では、表示されている問題によって影響を受けるオブジェクトの自動スキーマの変換を実行し、スキーマの変換を続行する前に確認のユーザーに求めます。 ユーザーできます推奨のコードの変更を確認し、いずれかで承認または拒否任意の特定のデータベース オブジェクトのすべての変換。

DMA では、Microsoft プログラム合成 (PROSE) テクノロジを使用して、コード修正を提案します。 詳細については[PROSE](https://microsoft.github.io/prose/)します。

## <a name="dma-v35"></a>DMA v3.5
DMA の v3.5 リリースには、次の追加機能が含まれています。
- (ベンチマーク テストでは、プロセスは 4 回よりも高速 DMA の以前のバージョンを示します)、Azure SQL Database に移行するための大幅なパフォーマンスの向上。
- メモリ フット プリントはさらに、移行のワークフローの安定性を向上させるために最適化されています。
- (既に、評価を実行し、移行前に重大なスキーマ オブジェクトのアドレスを指定した) 場合は、スキーマとデータの移行中に評価をスキップする権限です。
- レガシ バージョンの SQL Server のアップグレードを実行するオンプレミスにする場合に以降のバージョンまたは Azure Vm 上の SQL Server にバックアップ ファイルは、無効なネットワーク共有のパスを指定した場合のクラッシュのツールを使用して、問題に対処するための修正。

## <a name="dma-v34"></a>DMA v3.4
DMA の v3.4 リリースには、次の追加機能が含まれています。
- Azure SQL Database への移行のソースとして SQL Server 2017 をサポートします。
- 安定性、パフォーマンス、および評価ルールの正確性を強化します。

## <a name="dma-v33"></a>DMA v3.3
DMA の v3.3 リリースでは、Windows と Linux の両方での SQL Server 2017 の新しいバージョンに、オンプレミス SQL Server インスタンスを移行できるようにします。 Windows および Linux 用の全体的な移行ワークフローでは、同一の Linux の SQL Server 2017 への移行、いくつかの追加の考慮事項が必要です。

### <a name="specifying-the-back-up-path"></a>バックアップ パスを指定します。
Linux および Windows は、別のパスの形式を使用します。 その結果、SQL Server 2017 on Linux に移行する場合は、ユーザーが物理ファイルの場所へのパスのバージョンの Windows と Linux の両方を提供することが必要です。 物理ファイルの場所に応じて異なる方法で、パスの両方のバージョンを行うことができます。
物理バックアップ ファイルを実行しているコンピューターの場合。
- Linux を使用して、ネットワーク上の他のコンピューターとファイルを共有する 'samba' を共有します。
- Windows、Linux を実行しているコンピューター上に共有をマウントするのに 'mnt' コマンドを使用します。

> [!NOTE]
> 'Samba' 共有または 'mnt' コマンドを使用しての詳細については、この記事の範囲を超えては。

### <a name="migrating-windows-logins"></a>Windows ログインの移行
SQL Server 2017 on Linux では、Active Directory (AD) のログインの移行がサポートされている正式に、正常に機能する追加の構成が必要です。 この記事を参照してください[SQL Server on Linux での Active Directory 認証](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication)SQL Server 2017 on Linux での Active Directory ログインの設定の詳細について。 必要な構成を実行すると、セットアップが完了して、通常どおりに Active Directory ログインを移行することができます。 標準の SQL 認証は、追加の設定せず、期待どおりに動作します。

## <a name="dma-v32"></a>DMA v3.2
DMA の場合は v3.2 リリースには、次の追加機能が含まれています。

- スキーマとデータの移行が、オンプレミスの SQL Server データベースから Azure SQL Database に新しい移行ワークフローで有効です。
- Azure SQL Database へのスキーマの移行中に DMA はソース データベース オブジェクトのスクリプト、潜在的な互換性の問題を解決する方法について説明し、スキーマを Azure に配置されます。

## <a name="dma-v31"></a>DMA v3.1
DMA の v3.1 リリースには、次の追加機能が含まれています。

- サポートされていないシステム ストアド プロシージャ、および CLR オブジェクトのデータベースの照合順序の観点から Azure SQL Database の強化された評価の推奨事項を使用します。
- 互換性レベル 130、120、110、および 100 の Azure SQL Database に移行するときの評価のガイダンスです。

## <a name="dma-v30"></a>DMA v3.0
DMA の v3.0 リリースでは、関連する問題を修正するための包括的な推奨事項を提供する Azure SQL データベースの評価を拡張します。

- 移行を妨げる問題。
- 部分的に、または機能をサポートします。

## <a name="dma-v21"></a>DMA v2.1
DMA のバージョン 2.1 以降のリリースには、以下の追加が含まれています。
- スケールで評価を実行する、無人モードでの評価を実行するためのコマンドラインのサポート。 追加の詳細、情報の記事を参照してください[実行 Data Migration Assistant、コマンドラインから](dma-commandline.md)します。
- ユーザーが起動し、DMA を閉じるときにパフォーマンスの向上。
- SQL 接続のタイムアウトを構成する機能。追加の詳細、情報の記事を参照してください[Data Migration Assistant の構成設定](dma-configurationsettings.md)します。

## <a name="dma-v20"></a>DMA v2.0
DMA の v2.0 リリースには、記憶域の節約を最大化する適切な優先順位付きのテーブルを提供する向上の Stretch database 機能提案が含まれています。

## <a name="dma-v10"></a>DMA v1.0
DMA の v1.0 リリースは初期のリリースとを提供します。
- オンプレミス バージョンの SQL Server へのアップグレードに影響する問題の検出。 互換性の問題として、結果が記載されているし、これらは、次の領域に分類しています。
    - 重大な変更
    - 動作の変更
    - 非推奨の機能
- データベースのアップグレードから恩恵を受けるターゲット SQL Server プラットフォームの新機能の検出。 機能の推奨事項として、結果が記載されているし、これらは、次の領域に分類しています。
    - [パフォーマンス]
    - セキュリティ
    - ストレージ
-   評価を実行する最新のユーザー エクスペリエンス。

## <a name="see-also"></a>関連項目
[Data Migration Assistant の概要](../dma/dma-overview.md)
