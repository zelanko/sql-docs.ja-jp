---
title: "移行後の検証および最適化ガイド |Microsoft ドキュメント"
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 3
author: pelopes
ms.author: harinid
manager: 
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: d81eabfa1bdb5736bbf6f53ed34c2e1ac157e782
ms.contentlocale: ja-jp
ms.lasthandoff: 05/25/2017

---
# <a name="post-migration-validation-and-optimization-guide"></a>移行後の検証および最適化ガイド
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]post 移行手順がすべてのデータの精度と完全性を調整する際に非常に重要です。 だけでなく、ワークロードのパフォーマンスの問題を発見します。

# <a name="common-performance-scenarios"></a>パフォーマンスの一般的なシナリオ 
移行後に発生した、一般的なパフォーマンス シナリオの一部を次に示します[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]プラットフォームとの競合を解決する方法です。 Specifdic のシナリオがあります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行 (古いバージョンを新しいバージョン) と (Oracle、DB2、MySQL、Sybase) などの外部のプラットフォームを[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行します。

## <a name="Parameter Sniffing"></a>パラメーター スニッフィングに対する感度

**適用されます:** (Oracle、DB2、MySQL、Sybase) などの外部のプラットフォームを[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行します。

> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行には、この問題は、ソースに存在していた場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の新しいバージョンに移行する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]として-はいないこのシナリオに対応します。 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データの分布を入力用に最適化された、パラメーター化と再利用可能なプランを生成する最初のコンパイル時の入力パラメーターを見つけ出す機能を使用してストアド プロシージャでクエリ プランをコンパイルします。 ストアド プロシージャがない場合でも、単純なプランを生成するほとんどのステートメントがパラメーター化です。 プランがキャッシュされると、後に、以前にキャッシュされたプランを将来実行する任意に割り当てます。
潜在的な問題は、その最初のコンパイル使用いない場合、最も一般的なパラメーターのセットは通常のワークロードの場合に発生します。 さまざまなパラメーターは、同じ実行プランは非効率的になります。

### <a name="steps-to-resolve"></a>解決する手順

1.    使用して、`RECOMPILE`ヒント。 プランは、各パラメーターの値に適応するたびに計算されます。
2.    オプションを使用するストアド プロシージャの書き直し`(OPTIMIZE FOR(<input parameter> = <value>))`です。 使用する値に適したの作成および保守をパラメーター化された値を効率的に 1 つのプランは、関連するワークロードの大半を決定します。
3.    プロシージャ内のローカル変数を使用して、ストアド プロシージャを書き直してください。 これで、オプティマイザーは、結果のパラメーター値に関係なく同じプランの見積もり、密度ベクトルを使用します。
4.    オプションを使用するストアド プロシージャの書き直し`(OPTIMIZE FOR UNKNOWN)`です。 ローカル変数の手法を使用する場合と同様です。
5.    ヒントを使用するクエリを書き直す`DISABLE_PARAMETER_SNIFFING`です。 同じ影響を与えるとしてパラメーターを見つけ出す完全に無効にすると、によってローカル変数の手法を使用する場合を除き、 `OPTION(RECOMPILE)`、`WITH RECOMPILE`または`OPTIMIZE FOR <value>`を使用します。

> [!TIP] 
> 活用、[!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)]場合、これは、問題をすばやく識別する計画の分析機能します。 詳細については、使用可能な[ここ](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/)です。

## <a name="Missing indexes"></a>欠落したインデックス

**適用されます:** (Oracle、DB2、MySQL、Sybase) などの外部のプラットフォームと[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行します。

正しくないか、不足しているインデックスは、余分なメモリにつながる追加の I/O と CPU の浪費されているとします。 これによりを使用するなどの作業負荷プロファイルが変更されたためさまざまな述語の場合、既存の無効化インデックスの設計。 不適切なインデックス作成方法またはワークロードのプロファイルの変更の証拠は、次のとおりです。
-   複製で、ほとんど使用されないを重複していると完全に使用されていないインデックスを探します。
-   更新プログラムに使用されていないインデックスを持つ特別な注意します。

### <a name="steps-to-resolve"></a>解決する手順

1.    インデックスが存在しない参照をすべてのグラフィカル実行プランを利用します。
2.    によって生成された提案をインデックス[データベース エンジン チューニング アドバイザー](../tools/dta/tutorial-database-engine-tuning-advisor.md)です。
3.    活用、[欠落インデックス DMV](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)により、または、 [SQL Server パフォーマンス ダッシュ ボード](https://www.microsoft.com/en-us/download/details.aspx?id=29063)です。
4.    インデックスのすべての参照がヒント/にハードコーディング、データベースの既存のプロシージャおよび関数の場合も、不足している、重複する、冗長、めったに使用される、完全に使用されていないインデックスに関する洞察を提供する既存の Dmv を使用できる既存のスクリプトを活用します。 

> [!TIP] 
> このような既存のスクリプトの例として、[インデックスの作成](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation)と[インデックス情報](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information)です。 

## <a name="Inability to use predicates"></a>データのフィルター述語の機能を利用できません。

**適用されます:** (Oracle、DB2、MySQL、Sybase) などの外部のプラットフォームと[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行します。

> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行には、この問題は、ソースに存在していた場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の新しいバージョンに移行する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]として-はいないこのシナリオに対応します。

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]クエリ オプティマイザーはコンパイル時に認識されている情報のみを考慮することができます。 ワークロードは、実行時にのみが知っていることができますを述語に依存する場合は、不適切なプランの選択の可能性が向上します。 高品質のプランでは、述語がある必要があります**検索**、または**S**検索**Arg**ドキュメント**できません**です。

非検索述語の例をいくつか:
-   暗黙的なデータ変換、VARCHAR、NVARCHAR を VARCHAR に INT のいずれかのようにします。 実際の実行プランでランタイム CONVERT_IMPLICIT 警告を検索します。 1 つの型を変換すると、精度が失われるをこともあります。
-   などの複雑な不定式`WHERE UnitPrice + 1 < 3.975`、ではなく`WHERE UnitPrice < 320 * 200 * 32`です。
-   などの関数を使用して式`WHERE ABS(ProductID) = 771`または`WHERE UPPER(LastName) = 'Smith'`
-   ように、先頭のワイルドカード文字を使用した文字列`WHERE LastName LIKE '%Smith'`、ではなく`WHERE LastName LIKE 'Smith%'`です。

### <a name="steps-to-resolve"></a>解決する手順

1. 常に目的のターゲットとして変数およびパラメーターを宣言[データ型](../t-sql/data-types/data-types-transact-sql.md)です。 
  -   基になるテーブルで使用されるデータ型の情報を保持するシステム テーブル (ストアド プロシージャ、ユーザー定義関数またはビュー) など、データベースに格納されている任意のユーザー定義コード構造体を比較する可能性があります (など[sys.columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md))。
2. 過去の時点にすべてのコードをスキャンできない場合はし、同じ用途の任意の変数/パラメーターの宣言を一致するように、テーブルでのデータ型を変更します。
3. 次の構造の有用性を理由します。
  -   の述語として使用されている関数
  -   ワイルドカードを検索します。
  -   – 単票形式のデータに基づく複雑な式を計算列が永続化されたインデックスを作成できます。 これを代わりに作成する必要性を評価します。

> [!NOTE] 
> 上記のすべてが programmaticaly を実行することができます。

## <a name="Table Valued Functions"></a>テーブル値関数 (複数のステートメントとインライン) の使用

**適用されます:** (Oracle、DB2、MySQL、Sybase) などの外部のプラットフォームと[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行します。

> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]移行には、この問題は、ソースに存在していた場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の新しいバージョンに移行する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]として-はいないこのシナリオに対応します。

テーブル値関数は、代わりにビューを使用可能なテーブル データ型を返します。 ビューは、1 つに限定`SELECT`ステートメントでは、ユーザー定義関数がビューで使用可能なより多くのロジックを許可する追加のステートメントを含めることができます。

> [!IMPORTANT] 
> コンパイル時に、MSTVF (複数ステートメント テーブル値関数) の出力テーブルは作成されませんので、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ヒューリスティック、および行の推定を判断する実際の統計でクエリ オプティマイザーに依存しています。 基底のテーブルにインデックスを追加する場合でも、役立つこの予定はありません。 MSTVFs の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、MSTVF によって返される行の数が予期されたは、1 の固定の推定を使用して (以降で[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]推定を固定である 100 行)。

### <a name="steps-to-resolve"></a>解決する手順
1.    複数ステートメントの TVF が 1 つのステートメントのみである場合は、インライン TVF に変換します。

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress(@ID int)
    RETURNS @tblAddress TABLE
    ([Address] VARCHAR(60) NOT NULL)
    AS
    BEGIN
      INSERT INTO @tblAddress ([Address])
      SELECT TOP 1 [AddressLine1]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    RETURN
    END
    ```
    変換先 

    ```tsql
    CREATE FUNCTION dbo.tfnGetRecentAddress_inline(@ID int)
    RETURNS TABLE
    AS
    RETURN (
      SELECT TOP 1 [AddressLine1] AS [Address]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    )
    ```

2.    複雑な場合は、メモリ最適化テーブルまたは一時テーブルに格納されている中間結果を使用することを検討します。

##  <a name="Additional_Reading"></a> その他の情報  
 [クエリ ストアを使用する際の推奨事項](../relational-databases/performance/best-practice-with-the-query-store.md)  
[メモリ最適化テーブル](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
[ユーザー定義関数](../relational-databases/user-defined-functions/user-defined-functions.md)  
[変数をテーブルし、行の推定 - パート 1](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/11/30/table-variables-and-row-estimations-part-1/)  
[変数をテーブルし、行の推定 - パート 2](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/12/09/table-variables-and-row-estimations-part-2/)  
[実行プランのキャッシュと再利用](../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)

