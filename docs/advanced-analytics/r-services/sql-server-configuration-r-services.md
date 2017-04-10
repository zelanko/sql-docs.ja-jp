---
title: "SQL Server の構成 (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b08969f-b90b-46b3-98e7-0bf7734833fc
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# SQL Server の構成 (R Services)
このセクションの情報を使用しているコンピューターのハードウェアとネットワークの構成に一般的なガイダンスを提供するホストに [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。 に加えて、一般的な考慮 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] パフォーマンス チューニングで提供される情報、 [SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)します。

## プロセッサ

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] コンピューターに使用できるコアを使用して並列でタスクを実行できます。多くのコア、使用可能なパフォーマンスは向上します。  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 通常は、複数のユーザーが同時に使用する、データベース管理者は理想的なピーク ワークロードの計算をサポートするために必要とするコア数を決定する必要があります。 アルゴリズムが CPU にバインドされているコアの数には、IO 操作にバインドされたはプログラムが、中に多くのコアを備えた高速の Cpu がメリットを享受できます。

## [メモリ]

コンピューターで使用可能なメモリの量は、高度な分析アルゴリズムのパフォーマンスに大きな影響を与えることができます。 メモリ不足は、SQL の計算コンテキストを使用する場合、並列処理の次数にすることがあります。 処理可能なチャンク サイズ (読み取り操作ごとの行数) およびサポートできる同時セッションの数にも影響することができます。

32 GB の最小値を指定することが推奨されます。 32 GB を超える使用可能な場合は、読み取り操作のたびに複数の行を使用して、パフォーマンスを向上させる SQL データ ソースを構成することができます。

## 電源オプション

Windows オペレーティング システムで、 __高性能__ 電源オプションを使用する必要があります。 別の電源設定を使用して、パフォーマンスになりますが低下または整合性がありませんを使用する場合 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。

## ディスク IO

使用してトレーニングと予測のジョブ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] IO、本質的に、データベースが格納されているディスクの速度に依存し、連結されます。 ソリッド ステート ドライブ (SSD) などの高速なドライブが役立つ場合があります。 

ディスク I/O がディスクにアクセスする他のアプリケーションによっても影響を受ける: たとえば、他のクライアントがデータベースに対する処理を読み取ります。 ディスク IO パフォーマンスは、ファイル システムで使用されるブロック サイズなど、使用されているファイル システムの設定によっても影響することができます。 複数のドライブがある場合は、別のドライブでデータベースを保存 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] を要求するので [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 同じディスクを動作させないは、データベースに格納されたデータに対する要求として。

ディスク IO では、トレーニング中に何度も繰り返しを使用して RevoScaleR の分析関数を実行するときに、パフォーマンスも大幅に影響します。 たとえば、 `rxLogit`, 、`rxDTree`, 、`rxDForest` と `rxBTrees` 何度も繰り返しすべてを使用します。 データ ソースが場合 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 、これらのアルゴリズムがデータをキャプチャする最適化された一時ファイルを使用します。 これらのファイルが自動的にクリーンアップ、セッションが完了後します。 読み取り/書き込み操作のパフォーマンスの高いディスクを持つと、これらのアルゴリズムの全体的な経過時間を大幅に向上させることができます。

> [!NOTE]
> [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Windows オペレーティング システムの 8.3 ファイル名のサポートが必要です。 ドライブが 8.3 ファイル名をサポートするかどうかを確認するか、そうでない場合は、サポートを有効にする、fsutil.exe を使用することができます。 8.3 ファイル名で fsutil.exe の使用に関する詳細については、次を参照してください。 [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx)します。

### テーブルの圧縮

IO パフォーマンスには、圧縮または columstore インデックスを使用して多くの場合、向上できます。 一般に、データは、多くの場合、繰り返され、テーブル内の複数の列で、データを圧縮する場合に、これらの繰り返しの利用列ストア インデックスを使用しています。

列ストア インデックスは、テーブルへの挿入の多くがある場合を効率化できない場合がありますが、適切な選択肢は、データが静的かのみ変更頻度の低い場合。 列のストアが適切でない場合は、IO を向上させるために行の主なテーブルで圧縮を有効にするとを使用できます。

詳細については、次のドキュメントを参照してください。

* [データの圧縮](../../relational-databases/data-compression/data-compression.md)

* [テーブルまたはインデックスの圧縮の有効化](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [列ストア インデックス ガイド](Columnstore%20Indexes%20Guide.md)

## ページング ファイル

Windows オペレーティング システムでは、ページング ファイルを使用して、クラッシュ ダンプを管理し、仮想メモリ ページを格納するためです。 過度なページングが発生した場合は、コンピューター上の物理メモリを増やすことを検討してください。 複数の物理メモリ、ページングが消去されることはしません、ページングの必要性が減ります。

[ページのファイルが格納されているディスクの速度もパフォーマンスに影響します。 SSD 上のページング ファイルを格納するか、複数の Ssd の間で複数のページ ファイルを使用するには、パフォーマンスを向上できます。

参照してください [64 ビット バージョンの Windows 用の適切なページ ファイル サイズの決定方法](https://support.microsoft.com/en-us/kb/2860880) については、ページファイルのサイズを変更します。

## リソースのガバナンス

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 使用されるさまざまなリソースを制御するためのリソース管理をサポート [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。 たとえば、R によるメモリ消費の既定値は使用可能なメモリの合計の 20% に制限されて [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 これはいることを確認するため [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ワークフローに深刻な影響 R のジョブの実行時間の長いされません。 ただし、これらの制限は、データベース管理者によって変更できます。 

制限されたリソースが __MAX_CPU_PERCENT__, 、__MAX_MEMORY_PERCENT__, 、および __MAX_PROCESSES__します。 現在の設定を表示するには、これを使用 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] ステートメント。

```T-SQL
SELECT * FROM sys.resource_governor_external_resource_pools
``` 

場合 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は、主を R のサービスに使用することもに 40% または 60% まで MAX_CPU_PERCENT を増加します。 場合あります R セッションの数を使用して同じ [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 同時に 3 つすべてが高くなります。 割り当てられたリソースの値を変更するには使用 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] ステートメントです。 

この例では、メモリ使用量を 40% に設定します。

```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)
```
次の例は、次の 3 つすべての構成可能な値を設定します。
```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`
``` 

> [!NOTE]
> を直ちに有効にこれらの設定を変更するには、ステートメントを実行 `ALTER RESOURCE GOVERNOR RECONFIGURE` メモリ、CPU、または max プロセス設定を変更した後です。 

## 参照
[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)

[外部のリソース プールを作成します。](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [SQL Server R サービス パフォーマンス チューニング ガイド](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 
 [パフォーマンスのケース スタディ](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R とデータの最適化](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)