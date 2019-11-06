---
title: Data Migration Assistant の新機能 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 08/23/2019
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
ms.author: jtoland
ms.openlocfilehash: 2a4780c9be50275959a0f32091b90c518ccea124
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000595"
---
# <a name="whats-new-in-data-migration-assistant"></a>Data Migration Assistant の新機能
この記事では、Data Migration Assistant (DMA) の各リリースで追加された機能の一覧を示します。

## <a name="dma-v45"></a>DMA version 4.5

DMA の v2.0 リリースでは、ファイルシステムでホストされている SQL Server Integration Services (SSIS) パッケージを Azure SQL Database または Azure SQL Database マネージインスタンスに移行するための評価がサポートされています。

## <a name="dma-v44"></a>DMA v1.0

Version 4.4 の DMA リリースでは、Azure Migrate に評価をアップロードすることがサポートされています。

## <a name="dma-v43"></a>DMA v1.0

バージョン4.3 の DMA では、次の機能がサポートされています。

* ワークロード評価に基づく Azure SQL Database マネージインスタンスの SKU に関する推奨事項。
* RDS SQL Server 評価のソースとして使用されます。
* ターゲットとして Azure SQL Database マネージインスタンスのエージェントジョブの評価。
* 特定の評価規則を無視する機能。DMA で構成された ' ignoreErrorCodes ' プロパティに指定されているエラーコードの一覧は、DMA 評価の結果に表示されません。
* ジョブアクティビティステップでの T-sql クエリの評価と適切な推奨事項の提供
* 拡張イベントの評価 (パブリックプレビュー)。

さらに、このリリースの DMA では、データベース内の多数のスキーマオブジェクトを処理するパフォーマンスが向上し、に関連するバグの修正が行われています。

* ネイティブコンパイルを使用してコンパイルされたプロシージャ (場合によっては)。
* 複雑なデータベーススキーマ。

## <a name="dma-v42"></a>DMA v5.0

バージョン4.2 の DMA リリースでは、オンプレミスの SQL Server から Azure SQL Database マネージインスタンスに移行するときに、1つまたは複数のサーバーインスタンスのターゲット準備状態評価のためのコマンドラインサポートが提供されます。 DMA コマンドラインを使用して、データベーススキーマに関するメタデータを収集し、ブロッカーを検出し、Azure SQL Database マネージインスタンスへの移行に影響する部分的にサポートされている機能またはサポートされていない機能について学習できるようになりました。 その後、提供された Power BI テンプレートを使用して結果を表示できます。

## <a name="dma-v41"></a>DMA version 4.1

Version 4.1 リリースの DMA では、Azure SQL Database Managed Instance に移行するオンプレミスの SQL Server データベースの包括的な評価のサポートが導入されています。

評価ワークフローは、Azure SQL Database Managed Instance への移行に影響する可能性がある次の問題を検出するのに役立ちます。

* サポート**されていない機能または部分的にサポートされる機能**。 DMA は、ターゲット Azure SQL Database Managed Instance で部分的にサポートされているかサポートされていない使用中の機能について、ソース SQL Server データベースを評価します。 このツールでは、一連の推奨事項、Azure で利用可能なその他のアプローチ、および移行プロジェクトを計画する際にお客様がこの情報を考慮できるようにするための対策を講じます。

* **互換性の問題**。 DMA は、次の領域に関連する互換性の問題も識別します。

  * 重大な変更:対象のデータベースに移行する機能を損なう可能性のある特定のスキーマオブジェクト。  これらのスキーマオブジェクトは、データベースの移行後に修正することをお勧めします。
  * 動作の変更:報告されたスキーマオブジェクトは引き続き機能しますが、パフォーマンスの低下など、動作が異なる場合があります。
  * 情報に関する問題:これらのオブジェクトは移行に影響を与えませんが、機能 SQL Server のリリースで非推奨とされる可能性があります。

評価が完了したら、 [Azure Database Migration Service](https://azure.microsoft.com/services/database-migration/) (DMS) を使用して、SQL Server データベースの Azure SQL Database Managed Instance への移行を実行します。  DMS では、[オフライン](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)(1 回限り) と[オンライン](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)(最小限のダウンタイム) のデータベース移行の両方がサポートされており、Azure SQL Database Managed Instance になります。

## <a name="dma-v40"></a>DMA v4.0

バージョン4.0 の DMA では、Azure SQL Database SKU の推奨事項が導入されています。これにより、ユーザーは、データベースをホストしているコンピューターから収集されたパフォーマンスカウンターに基づいて、推奨される最小 Azure SQL Database SKU を特定できます。 この機能では、価格レベル、コンピューティングレベル、最大データサイズに関連する推奨事項に加え、月あたりの推定コストも提供します。 また、すべてのデータベースを Azure に一括してプロビジョニングする機能も提供されます。

> [!NOTE]
> 現在、この機能は、コマンドラインインターフェイス (CLI) を介してのみ使用できます。

詳細については、[オンプレミスデータベースの適切な AZURE SQL DATABASE SKU の特定に](dma-sku-recommend-sql-db.md)関する記事を参照してください。

## <a name="dma-v36"></a>DMA version 3.6

バージョン3.6 の DMA リリースでは、最も一般的な移行ブロックの影響を受けるスキーマオブジェクトに対して "自動修正" が導入されています。

このリリースでは、次の移行ブロックと動作の変更に関する問題の autofix が提供されています。

* 非修飾結合構文を使用するスキーマオブジェクト。
* レガシ RAISEERROR ステートメントを使用するスキーマオブジェクト。
* Order By 整数リテラルを使用する SQL ステートメント。

DMA は、一覧にある問題の影響を受けるオブジェクトに対してスキーマの自動変換を実行し、スキーマ変換を続行する前にユーザーに確認を求めるメッセージを表示します。 ユーザーは、提案されたコードの変更を確認し、特定のデータベースオブジェクトのすべての変換を受け入れるか拒否するかを選択できます。

DMA は、Microsoft プログラム合成 (PROSE) テクノロジを使用して、コード修正を提案します。 [PROSE](https://microsoft.github.io/prose/)の詳細については、こちらを参照してください。

## <a name="dma-v35"></a>DMA version 3.5

Version 3.5 リリースの DMA には、次の追加機能が含まれています。

* Azure SQL Database に移行する場合のパフォーマンスが大幅に向上しました (ベンチマークテストでは、以前のバージョンの DMA よりも4倍高速になっています)。
* メモリフットプリントは、移行ワークフローの安定性を向上させるためにさらに最適化されています。
* スキーマおよびデータの移行中に評価をスキップする機能 (既に評価を実行済みで、移行前にスキーマオブジェクトの互換性を解消している場合)。
* 古いバージョンの SQL Server オンプレミスからそれ以降のバージョンへのアップグレードを実行する場合、または Azure Vm 上で SQL Server する場合に、バックアップファイルに無効なネットワーク共有パスが指定されているときに、ツールがクラッシュする問題に対処するための修正。

## <a name="dma-v34"></a>DMA v3.4

バージョン3.4 の DMA には、次の追加情報が含まれています。

* Azure SQL Database への移行のソースとして SQL Server 2017 がサポートされます。
* 安定性、パフォーマンス、および評価ルールの正確性に関する機能強化。

## <a name="dma-v33"></a>DMA v3.3

バージョン3.3 の DMA リリースでは、Windows と Linux の両方で、オンプレミスの SQL Server インスタンスを SQL Server 2017 の新しいバージョンに移行できます。 Windows と Linux の移行の全体的なワークフローは同じですが、Linux 用の SQL Server 2017 に移行する場合は、いくつかの追加の考慮事項が必要です。

### <a name="specifying-the-back-up-path"></a>バックアップパスの指定

Linux と Windows では、異なるパス形式を使用します。 結果として、Linux 上の SQL Server 2017 に移行するには、ユーザーがパスの Windows と Linux の両方のバージョンを物理ファイルの場所に提供する必要があります。 物理ファイルの場所に応じて、パスの両方のバージョンをさまざまな方法で指定できます。
物理バックアップファイルが、を実行しているコンピューター上にある場合は、次のようになります。

* Linux では、"samba" 共有を使用して、ネットワーク上の他のコンピューターとファイルを共有します。
* Windows では、' mnt ' コマンドを使用して、Linux を実行しているコンピューターに共有をマウントします。

> [!NOTE]
> ' Samba ' 共有または ' mnt ' コマンドの使用の詳細については、この記事では説明しません。

### <a name="migrating-windows-logins"></a>Windows ログインの移行

Active Directory (AD) ログインの移行は Linux 上の SQL Server 2017 で正式にサポートされていますが、正常に機能するためには追加の構成が必要です。 Linux での SQL Server 2017 での Active Directory ログインの設定の詳細については、 [SQL Server on Linux での認証の Active Directory](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication)に関する記事を参照してください。 必要な構成を実行すると、セットアップが完了し、Active Directory ログインを通常どおりに移行できるようになります。 標準の SQL 認証は、追加の設定を行わなくても期待どおりに動作します。

## <a name="dma-v32"></a>DMA v3.2

バージョン3.2 の DMA には、次の追加機能が含まれています。

* スキーマとデータの移行は、新しい移行ワークフローで Azure SQL Database するために、オンプレミスの SQL Server データベースから有効になります。
* Azure SQL Database へのスキーマの移行中に、ソースデータベースオブジェクトに対して DMA スクリプトを実行し、潜在的な互換性の問題を修正してから Azure にスキーマをデプロイする方法に関するガイダンスを提供します。

## <a name="dma-v31"></a>DMA v3.1

バージョン3.1 の DMA には、次の追加情報が含まれています。

* データベース照合順序、サポートされていないシステムストアドプロシージャの使用、および CLR オブジェクトに関して、Azure SQL データベースの評価に関する推奨事項が改善されました。
* Azure SQL データベースに移行するときの互換性レベル130、120、110、および100の評価ガイダンス。

## <a name="dma-v30"></a>DMA v3.0

Version 3.0 リリースの DMA では、Azure SQL database の評価が拡張され、に関連する問題を修正するための包括的な推奨事項が提供されます。

* 移行のブロックの問題。
* 部分的またはサポートされていない機能と機能。

## <a name="dma-v21"></a>DMA v2.1

Version 2.1 リリースの DMA には、次の追加機能が含まれています。

* 評価を大規模に実行するのに役立つ無人モードで評価を実行するためのコマンドラインサポート。 詳細については、「[コマンドラインから Data Migration Assistant を実行](dma-commandline.md)する」を参照してください。
* ユーザーが DMA を起動して閉じるときのパフォーマンスが向上しました。
* SQL 接続のタイムアウトを構成する権限です。詳細については、「 [Data Migration Assistant の構成設定](dma-configurationsettings.md)」を参照してください。

## <a name="dma-v20"></a>DMA v2.0

V2.0 リリースの DMA には、ストレージの節約を最大化する適切な優先順位が付けられた拡張データベース機能の推奨事項が含まれています。

## <a name="dma-v10"></a>DMA v1.0

DMA の v1.0 リリースは最初のリリースであり、次の機能を備えています。

* オンプレミスバージョンの SQL Server へのアップグレードに影響する可能性がある問題の検出。 すべての結果は互換性の問題として記述されており、次の領域に分類されています。
  * 互換性に影響する変更
  * 動作の変更
  * 非推奨の機能
* アップグレード後にデータベースが恩恵を受けることのできるターゲット SQL Server プラットフォームの新機能の検出。 すべての結果は、機能に関する推奨事項として説明されており、次の領域に分類されています。
  * パフォーマンス
  * セキュリティ
  * ストレージ
* 評価を実行する最新のユーザーエクスペリエンス。

## <a name="see-also"></a>関連項目

[Data Migration Assistant の概要](../dma/dma-overview.md)
