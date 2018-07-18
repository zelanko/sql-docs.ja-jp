---
title: Data Migration Assistant (SQL Server) の新 |Microsoft Docs
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 620590f03bf429dbc1633a1f78bb921def5fd585
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982154"
---
# <a name="whats-new-in-data-migration-assistant"></a>Data Migration Assistant の新します。
このトピックでは、各リリースで追加の Data Migration Assistant (DMA) を使用します。

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
- (既に評価を実行し、移行前に重大なスキーマ オブジェクトのアドレスを指定した) 場合は、スキーマとデータの移行中に評価をスキップする権限です。
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
SQL Server 2017 on Linux では、Active Directory (AD) のログインの移行がサポートされている正式に、正常に機能する追加の構成が必要です。 トピックを参照してください[SQL Server on Linux での Active Directory 認証](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication)の SQL Server 2017 on Linux での Active Directory ログインの設定に関する詳細情報。 必要な構成を実行すると、セットアップが完了して、通常どおりに Active Directory ログインを移行することができます。 標準の SQL 認証は、追加の設定せず、期待どおりに動作します。

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
- スケールで評価を実行する、無人モードでの評価を実行するためのコマンドラインのサポート。 追加の詳細をトピックを参照してください[実行 Data Migration Assistant、コマンドラインから](dma-commandline.md)します。
- ユーザーが起動し、DMA を閉じるときにパフォーマンスの向上。
- SQL 接続のタイムアウトを構成する機能。追加の詳細をトピックを参照してください[Data Migration Assistant の構成設定](dma-configurationsettings.md)します。

## <a name="dma-v20"></a>DMA v2.0
DMA の v2.0 リリースには、記憶域の節約を最大化する適切な優先順位付きのテーブルを提供する向上の Stretch database 機能提案が含まれています。

## <a name="dma-v10"></a>DMA v1.0
DMA の v1.0 リリースは初期のリリースとを提供します。
- オンプレミス バージョンの SQL Server へのアップグレードに影響する問題の検出。 互換性の問題として、結果が記載されているし、これらは、次の領域に分類されます。
    - 重大な変更
    - 動作の変更
    - 非推奨の機能
- データベースのアップグレードから恩恵を受けるターゲット SQL Server プラットフォームの新機能の検出。 機能の推奨事項として、結果が記載されているし、これらは、次の領域に分類されます。
    - [パフォーマンス]
    - Security
    - ストレージ
-   評価を実行する最新のユーザー エクスペリエンス。

## <a name="see-also"></a>参照
[Data Migration Assistant の概要](../dma/dma-overview.md)
