---
title: "データ Migration Assistant (SQL Server) の新機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/03/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords: Data Migration Assistant, new features
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07d72eb6c4d40c3e61f4292616f9eda99d6d4742
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="whats-new-in-data-migration-assistant"></a>データ Migration Assistant の新機能

このトピックでは、各リリースで追加のデータ移行アシスタント (DMA) が一覧表示します。

## <a name="dma-v33"></a>DMA v3.3
DMA の v3.3 リリースでは、新しいバージョンの Windows と Linux の両方で、SQL Server 2017 を内部設置型 SQL Server インスタンスを移行できるようにします。 Windows と Linux の全体的な移行ワークフローでは、同じ for Linux は、SQL Server 2017 への移行には、いくつかの追加の考慮事項が必要です。

### <a name="specifying-the-back-up-path"></a>バックアップ パスを指定します。
Linux および Windows は、別のパスの形式を使用します。 その結果、Linux 上の SQL Server 2017 への移行には、ユーザーが Windows と Linux の両方のバージョンの物理ファイルの場所へのパスを指定することが必要です。 物理ファイルの場所に応じてさまざまな方法でこれを実現します。
物理的なバックアップ ファイルが実行しているコンピューター上にある場合は。
- Linux を使用して、ネットワーク上の他のコンピューターとファイルを共有する 'samba' を共有します。
-   Windows では、Linux を実行しているコンピューター上に共有をマウント 'やり' コマンドを使用します。

> [!NOTE]
> 'Samba' 共有または 'やり' コマンドを使用しての詳細については、この記事の範囲を超えています。

### <a name="migrating-windows-logins"></a>移行中の Windows ログイン
Linux 上の SQL Server 2017 では、Active Directory (AD) のログインの移行がサポートされている正式に、正常に機能する追加の構成が必要です。 トピックを参照してください[Linux に SQL Server と Active Directory 認証](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-active-directory-authentication)詳細については、Linux 上の SQL Server 2017 上の Active Directory のログインを設定します。 その後、セットアップが完了したら、Active Directory のログインを通常どおりに移行することができます。 標準の SQL 認証は、任意の追加設定せず、期待どおりに動作します。

## <a name="dma-v32"></a>DMA v3.2
DMA の場合は v3.2 リリースには、次の追加機能が含まれています。

- スキーマとデータの移行が、内部設置型 SQL Server データベースから Azure SQL データベースを新しい移行ワークフローで有効です。

- Azure SQL Database には、スキーマの移行中には、DMA はソース データベース オブジェクトのスクリプト、潜在的な互換性の問題を解決する方法について説明しを Azure に、スキーマを展開します。

## <a name="dma-v31"></a>DMA v3.1
DMA の v3.1 リリースには、次の追加機能が含まれています。

- 強化された評価に関する推奨事項の Azure SQL データベース、データベースの照合順序の観点からは、サポートされていないシステム ストアド プロシージャ、および CLR オブジェクトの使用します。

- 互換性レベル 130、120、110、および 100 の Azure SQL データベースを移行する場合の評価のガイダンスです。

## <a name="dma-v30"></a>DMA v3.0
DMA の v3.0 リリースは、Azure SQL データベースの評価に関連する問題を修正するための包括的な推奨事項を示しませんを拡張します。

- ブロックの問題を移行します。

- 部分的にかの特性と機能がサポートされていません。

## <a name="dma-v21"></a>DMA v2.1
DMA のバージョン 2.1 以降のリリースには、次の追加が含まれています。
- スケールで評価を実行するのに役立つ、無人モードでの評価を実行するためのコマンド ライン サポートします。 詳細については、トピックを参照してください[実行データ Migration Assistant コマンドラインから](dma-commandline.md)です。

- ユーザーが起動し、DMA を閉じるときにパフォーマンスの向上。

- SQL 接続のタイムアウトを構成する機能。詳細については、トピックを参照してください[データ Migration Assistant の構成設定](dma-configurationsettings.md)です。

## <a name="dma-v20"></a>DMA v2.0
DMA のバージョン 2.0 リリースには、強化されたストレッチ データベース機能に関する推奨事項記憶域削減効果を最大限活用する適切な優先順位付けされたテーブルを提供するにはが含まれています。

## <a name="dma-v10"></a>DMA v1.0
DMA の v1.0 リリースは、最初のリリースのとなります。
- オンプレミス バージョンの SQL Server へのアップグレードに影響する問題の検出。 互換性の問題として、発見が説明されているし、これらは、次の領域に分類されます。
    -   重大な変更
    - 動作の変更
    - 非推奨機能

- データベースのアップグレードから利点を活用できるターゲット SQL Server プラットフォームの新機能の検出。 機能の推奨事項として、発見が説明されているし、それらは、次の領域に分類されます。
    - [パフォーマンス]
    - Security
    - ストレージ

-   最新のユーザー エクスペリエンスの評価を実行します。

## <a name="see-also"></a>参照

[Migration Assistant のデータの概要](../dma/dma-overview.md)
