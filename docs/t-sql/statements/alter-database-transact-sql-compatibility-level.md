---
title: "ALTER DATABASE 互換性レベル (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COMPATIBILITY_LEVEL_TSQL
- COMPATIBILITY_LEVEL
dev_langs: TSQL
helpviewer_keywords:
- 80 compatibility level
- ALTER DATABASE statement, compatibility levels
- 90 compatibility level
- compatibility levels [SQL Server]
- 100 compatibility level
ms.assetid: ca5fd220-d5ea-4182-8950-55d4101a86f6
caps.latest.revision: "89"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 62a9e4eec99073e63d53c2d610a7527fbe5f9c91
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="alter-database-transact-sql-compatibility-level"></a>ALTER DATABASE (TRANSACT-SQL) の互換性レベル
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  
データベースの特定の動作の指定されたバージョンに合うように設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 その他の ALTER DATABASE オプションについては、次を参照してください。 [ALTER DATABASE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE database_name   
SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
 COMPATIBILITY_LEVEL {140 | 130 | 120 | 110 | 100 | 90 | 80}  
 バージョンは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するデータベースを互換性のあるとします。 次の互換性レベルの値を構成できます。  
  
|Product|データベース エンジンのバージョン|互換性レベルの指定|サポートされる互換性レベルの値|  
|-------------|-----------------------------|-------------------------------------|------------------------------------------|  
|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|14|140|140, 130, 120, 110, 100|
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|12|130|140, 130, 120, 110, 100|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|13|130|130, 120, 110, 100|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|12|120|120, 110, 100|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|11|110|110, 100, 90|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|10.5|100|100, 90, 80|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|10|100|100, 90, 80|  
|SQL Server 2005|9|90|90, 80|  
|SQL Server 2000|8|80|80|  
  
> [!NOTE]  
>  **Azure SQL Database** V12 は 2014 年 12 月にリリースされました。 リリースの 1 つの側面ならなかったこと新しく作成されたデータベースの互換性レベルを 120 に設定します。 2015 では、SQL データベースは、既定値 120 のままであったにレベルが 130 のサポートを開始しました。  
> 
> 以降で**2016 年 6 月中旬**、Azure SQL データベースにおける既定の互換性レベルが 120 ではなく 130**新しく作成された**データベース。 2016 年 6 月中旬の前に作成された既存のデータベースは影響がなく、および、その現在の互換性レベル 100、110 (120) を維持します。 
> 
> 場合レベルが 130、データベースの一般的に、レベル 110 を使用する理由がある**基数の推定**アルゴリズムを参照してください[ALTER DATABASE SCOPED CONFIGURATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)、具体的には、そのキーワード LEGACY_CARDINALITY_ESTIMATION = ON です。  
>  
>  Azure SQL データベースで次の 2 つの互換性レベルの間で、最も重要なクエリのパフォーマンスの違いを評価する方法の詳細についてを参照してください[Azure SQL データベースの互換性レベル 130 でのクエリ パフォーマンスの向上](http://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)です。


 バージョンを調べるには、次のクエリ実行、[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続されています。  
  
```tsql  
SELECT SERVERPROPERTY('ProductVersion');  
```  
  
> [!NOTE]  
>  サポートされる互換性レベルによって異なる機能をすべて[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  

 現在の互換性レベルを特定するのには、クエリ、 **compatibility_level**の列[sys.databases &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
```tsql  
SELECT name, compatibility_level FROM sys.databases;  
```  
  
## <a name="remarks"></a>解説  
 すべてのインストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバージョンに既定の互換性レベルが設定されて、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 データベースがこのレベルに設定されていない限り、**モデル**データベースが互換性レベルを低くします。 以前のバージョンからのデータベースのアップグレードされると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は少なくとも最小のインスタンスを許可されている場合、データベースは、既存の互換性レベルを保持[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 許可されたレベルより低い互換性レベルでデータベースをアップグレードするには、最下位の互換性レベルに、データベースを設定します。 これはシステム データベースとユーザー データベースの両方に適用されます。 使用して**ALTER DATABASE**データベースの互換性レベルを変更します。 データベースの現在の互換性レベルを表示するには、クエリ、 **compatibility_level**内の列、 **sys.databases**カタログ ビューです。  

  
## <a name="using-compatibility-level-for-backward-compatibility"></a>旧バージョンとの互換性を維持するための互換性レベルの使用  
 互換性レベルは、サーバー全体ではなく、指定したデータベースの動作にのみ影響します。 互換性レベルのみの旧バージョンと部分の下位互換性を提供する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 以降 130 の互換モードで、新しいクエリ プランに影響を与える機能が追加されて新しい互換モードにのみです。 これは、クエリ プランの変更によってパフォーマンスの低下から発生するためのアップグレード中に、リスクを最小限に抑えるために追加されました。 アプリケーションの観点から目的は、最新の互換性レベルにするためには、制御された方法でですが、いくつかの新機能と、クエリ オプティマイザーのスペースでパフォーマンスの向上を継承するためにもです。 互換性レベルは、移行時の暫定的な手段として使用してください。互換性レベルの設定により動作を制御することで、バージョン間の動作の違いに対処することができます。 詳細については、アップグレードのベスト プラクティス、記事の後半を参照してください。  
  
 既存の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバージョンの動作の違いによって影響を受けるアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、互換性モードを新しいしてシームレスに動作するアプリケーションに変換します。 使用して**ALTER DATABASE**互換性レベル 130 に変更します。 データベースの新しい互換性設定されるときに有効、 **USE Database**が発行または既定のデータベースとしてそのデータベースに新しいログインを処理します。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ユーザーがデータベースに接続しているときに互換性レベルを変更すると、アクティブなクエリに対し誤った結果セットが生成される可能性があります。 たとえば、クエリ プランのコンパイル中に互換性レベルを変更すると、コンパイルされるプランは変更前の互換性レベルと変更後の互換性レベルの両方に基づいてしまう場合があります。その結果、誤ったプランが生成され、不正確な結果が発生する可能性があります。 さらに、プランがプラン キャッシュに置かれ後続のクエリにより再使用された場合、問題が複雑になることが考えられます。 不正確なクエリ結果を避けるため、データベースの互換性レベルを変更するときには次の手順に従うことをお勧めします。  
  
1.  ALTER DATABASE SET SINGLE_USER を使用してデータベースをシングル ユーザー アクセス モードに設定します。  
  
2.  データベースの互換性レベルを変更します。  
  
3.  ALTER DATABASE SET MULTI_USER を使用してデータベースをマルチユーザー アクセス モードにします。  
  
4.  データベースのアクセス モードの設定の詳細については、次を参照してください。 [ALTER DATABASE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="compatibility-levels-and-stored-procedures"></a>互換性レベルとストアド プロシージャ  
 ストアド プロシージャを実行すると、そのストアド プロシージャが定義されているデータベースの現在の互換性レベルが使用されます。 データベースの互換性設定が変更された場合、そのデータベースのすべてのストアド プロシージャは、設定に合わせて自動的に再コンパイルされます。  

## <a name="differences-between-compatibility-level-130-and-level-140"></a>互換性レベル 130 とレベル 140 の相違点  
このセクションでは、互換性レベルが 140 導入された新しい動作について説明します。

|以下の 130 の互換性レベルの設定|140 の互換性レベルの設定|  
|--------------------------------------------------|-----------------------------------------|  
|基数の推定値複数ステートメント テーブル値を参照するステートメントの関数が固定の行の推定値を使用します。|に対する基数の推定条件を満たすステートメントが参照する複数ステートメント テーブル値関数が関数の出力の実際の基数を使用します。  これが有効になって**実行をインターリーブ**複数ステートメント テーブル値関数です。|
|十分なメモリを要求するクエリをバッチ モードでは、結果をディスクに溢れが連続して実行に問題がある引き続きサイズを付与します。|十分なメモリ許可サイズが連続して実行のパフォーマンスが向上してが可能性がありますをディスクに溢れで結果を要求するクエリをバッチ モードです。  これが有効になって**バッチ モードのメモリ許可のフィードバック**のバッチ モード演算子溢れが発生した場合、キャッシュされたプランのメモリ許可サイズを更新するされます。 |
|過度なメモリを要求するクエリをバッチ モードでは、同時実行の問題の結果が連続して実行に問題がある引き続きサイズを付与します。|過度なメモリを要求するクエリをバッチ モードでは、同時実行の問題になるサイズにより、連続実行では同時実行性が改善されを付与します。  これが有効になって**バッチ モードのメモリ許可のフィードバック**過度な量が最初に要求した場合、キャッシュされたプランのメモリ許可サイズを更新するされます。|
|結合演算子を含むクエリをバッチ モードでは、入れ子になったループ、ハッシュ結合、およびマージ結合を含む 3 つの物理結合アルゴリズムの対象。  基数の推定が結合入力に対して適切でない場合は、不適切な結合アルゴリズムを選択することがあります。  このような場合は、パフォーマンスが低下し、不適切な結合アルゴリズムは、キャッシュされたプランが再コンパイルするまで、使用中は残ります。|呼ばれる追加の結合演算子がある**アダプティブ結合**です。 基数の推定が外部のビルドの結合入力に対して適切でない場合は、不適切な結合アルゴリズムを選択することがあります。  これが発生し、ステートメントは、アダプティブ結合の対象となるより小さな結合入力に使用する入れ子になったループとハッシュ結合に使用する大規模な結合の入力に動的に再コンパイルせずします。 |
|列ストア インデックスを参照する単純なプランは、バッチ モード実行の資格がありません。 |バッチ モード実行の条件に適合するプランを優先するため、列ストア インデックスを参照する単純なプランが破棄されます。|
|Sp_execute_external_script UDX 操作は、行のモードでのみ実行できます。|Sp_execute_external_script UDX 操作はバッチ モード実行の条件に適合します。|  
|複数ステートメントの TVF には、逐次的実行はありません。 |プランの品質を向上させるために複数ステートメントの Tvf の逐次的実行します。 |

SQL Server 2017 する前に SQL Server の以前のバージョンでは、トレース フラグ 4199 の下にあったの修正プログラムは既定で有効になりました。 互換モード 140 です。 トレース フラグ 4199 を SQL Server 2017 以降後にリリースされる新しいクエリ オプティマイザー修正プログラムに適用されます。 トレース フラグの 4199 については、次を参照してください。[トレース フラグ 4199](https://support.microsoft.com/en-us/kb/974006)です。  
  
## <a name="differences-between-compatibility-level-120-and-level-130"></a>レベル 120 とレベルの 130 の互換性の相違点  
このセクションでは、互換性レベル 130 で導入された新しい動作について説明します。   

  
|互換性レベル設定 120 以下|130 の互換性レベルの設定|  
|--------------------------------------------------|-----------------------------------------|  
|Insert select ステートメントでは、シングル スレッドです。|Insert select ステートメントで挿入では、マルチ スレッドは、または並列プランを持つことができます。|  
|メモリ最適化テーブルに対するクエリでは、シングル スレッドを実行します。|メモリ最適化テーブルに対するクエリは、並列プランを保持できます。|  
|SQL 2014 の基数推定機能を導入**CardinalityEstimationModelVersion =「120」**|さらに基数の推定 (CE)、クエリから表示される基数の推定モデルの 130 の改良点を計画します。 **CardinalityEstimationModelVersion =「130」**|  
|列ストア インデックスを持つ行モードではなくバッチ モードが変更されました。<br /><br /> 列ストア インデックスを持つテーブルでの並べ替えが行モードでは<br /><br /> ウィンドウ関数の集計が LAG など潜在顧客行モードで動作します。<br /><br /> 行のモードで運用されている複数の個別の句を持つ列ストア テーブルに対するクエリ<br /><br /> MAXDOP 1 または行モードで実行される直列プランで実行されているクエリ | 列ストア インデックスを持つ行モードではなくバッチ モードが変更されました。<br /><br /> 列ストア インデックスを持つテーブルでの並べ替えがバッチ モードです。<br /><br /> ウィンドウ集計の遅延やリードなど、バッチ モードで運用します。<br /><br /> 複数の distinct 句で列ストア テーブルに対するクエリがバッチ モードで動作します。<br /><br /> Maxdop1 または直列プランで実行されているクエリをバッチ モードで実行します。|  
| 統計は自動的に更新することができます。 | 統計を自動的に更新するロジックはより大規模なテーブルで積極的なです。  実際には、この場合は、顧客に表示されるパフォーマンスの問題クエリが新しく挿入された行がここで、統計が更新されていないこれらの値が含まれるが、頻繁に照会されますが減ります。 |  
| 既定でトレース 2371 は OFF です。[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。 | [トレース 2371](https://blogs.msdn.microsoft.com/psssql/2016/10/04/default-auto-statistics-update-threshold-change-for-sql-server-2016/)が既定で ON[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 トレース フラグ 2371 は、小さいまだ賢明優れた多数の行があるテーブル内の行のサブセットをサンプリングする自動統計更新を指示します。 <br/> <br/> 1 つの向上では、最近挿入された行にはサンプルが含まれます。 <br/> <br/> 別の向上はクエリ、更新の統計情報の処理を実行しているではなく、クエリをブロックしている間に実行します。 |  
| レベル 120 の場合、統計情報がによってサンプリングされた、*単一*-プロセスのスレッドします。 | によってレベル 130 の場合、統計のサンプリング、*マルチ*-プロセスをスレッドです。 |  
| 着信 253 の外部キーは、制限です。 | 指定されたテーブルは、最大 10,000 個の入力方向の外部キーまたは類似の参照で参照できます。 制限については、「 [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md)」を参照してください。 |  
|非推奨の MD2、MD4、MD5、SHA、SHA1、ハッシュ アルゴリズムが許可されます。|SHA2_256 および SHA2_512 のハッシュ アルゴリズムがのみが許可されます。|  
  
  
トレースの下にあったの修正プログラム フラグの以前のバージョンの 4199[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より前のバージョン[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]は既定で有効になっているようになりました。 互換モードは 130 です。 トレース フラグ 4199 を以降後にリリースされる新しいクエリ オプティマイザー修正プログラムの適用にすることができます[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 古いクエリ オプティマイザーを使用する[!INCLUDE[ssSDS](../../includes/sssds-md.md)]互換性レベル 110 を選択する必要があります。 トレース フラグの 4199 については、次を参照してください。[トレース フラグ 4199](https://support.microsoft.com/en-us/kb/974006)です。  
  
## <a name="differences-between-lower-compatibility-levels-and-level-120"></a>レベル 120 とより低い互換性レベルとの相違点  
 ここでは、互換性レベル 120 に導入された新しい動作について説明します。  
  
|互換性レベル設定 110 以下|互換性レベル設定 120|  
|--------------------------------------------------|-----------------------------------------|  
|以前のクエリ オプティマイザーが使用されます。|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、クエリ プランを作成し最適化するコンポーネントに大幅な改良が加えられました。 この新しいクエリ オプティマイザー機能は、データベース互換性レベル 120 を使用している場合にのみ利用できます。 これらの改良点を利用するには、データベースの互換性レベル 120 を使用して新しいデータベース アプリケーションを開発する必要があります。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から移行されたアプリケーションについては、良好なパフォーマンスが維持されているか、またはパフォーマンスが向上していることを確認するために慎重にテストを実行する必要があります。 パフォーマンスが低下する場合は、データベースの互換性レベルを 110 以前に設定して、古いクエリ オプティマイザーの方法を使用することができます。<br /><br /> データベースの互換性レベル 120 に設定した場合は、最新のデータ ウェアハウスと OLTP ワークロード向けにチューニングされた新しい基数推定機能が使用されます。 パフォーマンスの問題があるため、データベースの互換性レベルを 110 に設定、する前に、クエリ プランのセクションの推奨事項を参照してください、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [データベース エンジンの新](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md)トピックです。|  
|変換するときに互換性レベルが 120 未満の場合、言語設定が無視されますが、**日付**値を文字列値です。 この動作はのみに固有です、**日付**型です。 後述の「例」の例 B を参照してください。|変換するときに、言語設定は無視されませんが、**日付**値を文字列値です。|  
|EXCEPT 句の右側にある再帰参照によって、無限ループが作成されます。 後述の「例」の例 C では、この動作を示します。|EXCEPT 句の再帰参照によって、ANSI SQL 標準に準拠したエラーが生成されます。|  
|再帰 CTE では、重複する列名を使用できます。|再帰 CTE では、重複する列名を使用できません。|  
|無効化されたトリガーは、トリガーが変更されると有効になります。|トリガーを変更しても、トリガーの状態 (有効または無効) は変更されません。|  
|OUTPUT INTO テーブル句では、IDENTITY_INSERT SETTING = OFF が無視され、明示的な値を挿入できます。|IDENTITY_INSERT が OFF に設定されているときは、テーブルの ID 列に明示的な値を挿入できません。|  
|データベースの包含状態が PARTIAL に設定されている場合、MERGE ステートメントの OUTPUT 句にある $action フィールドを検証すると、照合順序のエラーが確認されることがあります。|MERGE ステートメントの $action 句によって返される値の照合順序は、サーバー照合順序ではなく、データベース照合順序です。また、照合順序の競合エラーは返されません。|  
|A **SELECT INTO**ステートメントは常にシングル スレッドの挿入操作を作成します。|A **SELECT INTO**ステートメントは、並列挿入操作を作成できます。 多数の行を挿入するときは、並列操作によってパフォーマンスを向上させることができます。|  
  
## <a name="differences-between-lower-compatibility-levels-and-levels-110-and-120"></a>レベル 120 とレベル 110 以下の互換性レベルの相違点  
 このセクションでは、互換性レベル 110 で導入された新しい動作について説明します。   このセクションはレベル 120 にも当てはまります。  
  
|100 以下に、互換性レベル設定|互換性レベル設定 110 以上|  
|--------------------------------------------------|--------------------------------------------------|  
|共通言語ランタイム (CLR) のデータベース オブジェクトは、CLR の Version 4 で実行されます。 ただし、CLR の Version 4 で導入されたいくつかの動作の変更が回避されます。 詳細については、次を参照してください。 [CLR 統合における新](../../relational-databases/clr-integration/clr-integration-what-s-new.md)です。|CLR のデータベース オブジェクトは、CLR の Version 4 で実行されます。|  
|XQuery 関数**文字列長**と**substring**各サロゲートを 2 つの文字としてカウントします。|XQuery 関数**文字列長**と**substring**各サロゲート文字 1 文字としてカウントします。|  
|PIVOT は再帰共通テーブル式 (CTE) のクエリで許可されます。 ただし、グループごとに複数の行がある場合、クエリは誤った結果を返します。|PIVOT は再帰共通テーブル式 (CTE) のクエリで許可されません。 エラーが返されます。|  
|RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材の暗号化を解除できます。|新素材は、RC4 または RC4_128 を使用して暗号化することはできません。 AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材の暗号化を解除できます。|  
|に対する CAST および CONVERT 操作の既定のスタイル**時間**と**datetime2**データ型は、計算列の式内のいずれかの型を使用する場合を除き、121 です。 計算列の場合、既定のスタイルは 0 です。 この動作は、計算列が作成されるとき、自動パラメーター化を含むクエリで使用されるとき、または制約の定義で使用されるときに、計算列に影響を与えます。<br /><br /> 例では、後述の「例 D では、スタイル 0 と 121 の違いを示します。 上記の動作については示しません。 日付と時刻のスタイルの詳細については、次を参照してください。 [CAST および CONVERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md).|互換性レベル 110 で CAST および CONVERT 操作の既定のスタイルで**時間**と**datetime2**データ型は常に 121 です。 クエリが古い動作に依存する場合は、110 より小さい互換性レベルを使用するか、または影響を受けるクエリで 0 スタイルを明示的に指定してください。<br /><br /> データベースを互換性レベル 110 にアップグレードしても、ディスクに格納されているユーザー データは変更されません。 このようなデータは手動で適切に修正する必要があります。 たとえば、SELECT INTO を使用して、前に説明した計算列の式を含むソースからテーブルを作成した場合は、計算列の定義自体ではなく、(スタイル 0 を使用する) データが格納されます。 このようなデータは、手動で更新してスタイル 121 に一致させる必要があります。|  
|型のリモート テーブル内の列**smalldatetime**はパーティション ビューで参照されるとしてマップ**datetime**です。 型でなければなりません (選択リスト内の同じ序数位置) でのローカル テーブルの対応する列**datetime**です。|型のリモート テーブル内の列**smalldatetime**はパーティション ビューで参照されるとしてマップ**smalldatetime**です。 型でなければなりません (選択リスト内の同じ序数位置) でのローカル テーブルの対応する列**smalldatetime**です。<br /><br /> 110 にアップグレードした後は、データ型の不一致により、分散パーティション ビューは失敗します。 これを解決するには、リモート テーブルでのデータ型を変更することによって**datetime**またはレベル以下を 100 にローカルのデータベースの互換性を設定します。|  
|SOUNDEX 関数では、次の規則を実装します。<br /><br /> 2 つの子音数を持つ同じ SOUNDEX コードの場合、1) 大文字の H または大文字の W は無視されます。<br /><br /> 2) 場合、最初の 2 文字*character_expression* SOUNDEX コードの同じ番号、両方の文字が含まれます。 最初の 2 文字の場合を除き、並んでいる一連の子音に SOUNDEX コードの同じ数値が割り当てられている場合、最初の文字以外はすべて除外されます。|SOUNDEX 関数では、次の規則を実装します。<br /><br /> 1) 場合、大文字の H または大文字の W の 2 つの分割数を持つ同じ SOUNDEX コード、右側の子音の子音は無視されます<br /><br /> 2) 一連の子音のサイド バイ サイドでは、SOUNDEX コードの同じ番号がある、すべての除外された場合、先頭を除く。<br /><br /> <br /><br /> その他のルールにより、SOUNDEX 関数で計算された値が、110 未満の互換性レベルで計算された値と異なる結果になる場合があります。 互換性レベル 110 へのアップグレード後に、SOUNDEX 関数を使用するインデックス、ヒープ、または CHECK 制約の再構築が必要になる場合があります。 詳細については、次を参照してください。 [SOUNDEX (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/soundex-transact-sql.md)|  
  
## <a name="differences-between-compatibility-level-90-and-level-100"></a>互換性レベル 90 とレベル 100 の相違点  
 このセクションでは、互換性レベル 100 で導入された新しい動作について説明します。  
  
|90 の互換性レベルの設定|互換性レベルの設定は 100|影響度|  
|----------------------------------------|-----------------------------------------|---------------------------|  
|複数ステートメントのテーブル値関数が作成されるとき、QUOTED_IDENTIFER 設定はセッション レベルの設定に関係なく常に ON に設定されます。|複数ステートメントのテーブル値関数が作成されるとき、QUOTED IDENTIFIER のセッション設定が受け入れられます。|Medium|  
|Create または alter パーティション関数と**datetime**と**smalldatetime**してから、US_English、言語設定と仮定した場合、関数内のリテラルが評価されます。|現在の言語設定を使用して評価**datetime**と**smalldatetime**パーティション関数内のリテラルです。|Medium|  
|INSERT ステートメントと SELECT INTO ステートメントで FOR BROWSE 句は許可されます (ただし無視されます)。|INSERT ステートメントと SELECT INTO ステートメントで FOR BROWSE 句は許可されません。|Medium|  
|OUTPUT 句でフルテキスト述語を使用できます。|OUTPUT 句でフルテキスト述語を使用できません。|Low|  
|CREATE FULLTEXT STOPLIST、ALTER FULLTEXT STOPLIST、および DROP FULLTEXT STOPLIST はサポートされていません。 システム ストップリストは、自動的に新しいフルテキスト インデックスに関連付けられます。|CREATE FULLTEXT STOPLIST、ALTER FULLTEXT STOPLIST、および DROP FULLTEXT STOPLIST はサポートされています。|Low|  
|MERGE は予約されたキーワードとして適用されません。|MERGE は完全に予約されたキーワードです。 MERGE ステートメントは、100 と 90 の両方の互換性レベルでサポートされます。|Low|  
|使用して、 \<dml_table_source > 引数を INSERT ステートメントの構文エラーが発生します。|入れ子になった INSERT、UPDATE、DELETE、または MERGE ステートメント内の OUTPUT 句の結果をキャプチャして、対象のテーブルまたはビューに挿入することができます。 これを使用して、 \<dml_table_source >、INSERT ステートメントの引数。|Low|
|NOINDEX が指定されていない場合、DBCC CHECKDB または DBCC CHECKTABLE は、1 つのテーブルまたはインデックス付きビューとそのすべての非クラスター化インデックスおよび XML インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 空間インデックスはサポートされません。|NOINDEX が指定されていない場合、DBCC CHECKDB または DBCC CHECKTABLE は、1 つのテーブルとそのすべての非クラスター化インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 ただし、XML インデックス、空間インデックス、およびインデックス付きビューでは、既定で物理的な一貫性のみがチェックされます。<br /><br /> インデックス付きビュー、XML インデックス、および空間インデックスの論理チェックが実行 WITH EXTENDED_LOGICAL_CHECKS が指定されている場合、場所を表示します。 既定では、論理的な一貫性のチェック前に物理的な一貫性がチェックされます。 NOINDEX も指定されている場合は、論理チェックのみが実行されます。|Low|  
|データ操作言語 (DML) ステートメントで OUTPUT 句を使用した場合、ステートメントの実行時に実行時エラーが発生すると、トランザクション全体が終了し、ロールバックされます。|データ操作言語 (DML) ステートメントで OUTPUT 句を使用した場合、ステートメントの実行時に実行時エラーが発生したときの動作は、SET XACT_ABORT 設定によって異なります。 SET XACT_ABORT が OFF の場合は、OUTPUT 句を使用している DML ステートメントでステートメント中断エラーが発生すると、ステートメントは終了しますが、バッチの実行は続行され、トランザクションはロールバックされません。 SET XACT_ABORT が ON の場合は、OUTPUT 句を使用している DML ステートメントで実行時エラーが発生すると、バッチが終了し、トランザクションはロールバックされます。|Low|  
|CUBE および ROLLUP は予約されたキーワードとして適用されません。|CUBE および ROLLUP は、GROUP BY 句内では予約されたキーワードです。|Low|  
|厳密な検証が、XML の要素に適用される**anyType**型です。|Lax 検証がの要素に適用される、 **anyType**型です。 詳細については、次を参照してください。[ワイルドカード コンポーネントと内容検証](../../relational-databases/xml/wildcard-components-and-content-validation.md)です。|Low|  
|特殊な属性**xsi:nil**と**xsi:type**クエリを実行したり、データ操作言語ステートメントで変更することはできません。<br /><br /> つまり、`/e/@xsi:nil`中に失敗する`/e/@*`は無視、 **xsi:nil**と**xsi:type**属性。 ただし、`/e`を返します、 **xsi:nil**と**xsi:type**属性との整合性`SELECT xmlCol`場合でも、`xsi:nil = "false"`です。|特殊な属性**xsi:nil**と**xsi:type**は通常の属性として保存して照会および変更できます。<br /><br /> たとえば、クエリの実行`SELECT x.query('a/b/@*')`を含むすべての属性を返します**xsi:nil**と**xsi:type**です。 クエリでこれらの型を除外する置換`@*`で`@*[namespace-uri(.) != "` *xsi 名前空間 uri を挿入*`"`および not`(local-name(.) = "type"`または`local-name(.) ="nil".`|Low|  
|XML 定数文字列値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime 型に変換するユーザー定義関数は、"決定的" とマークされます。|XML 定数文字列値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime 型に変換するユーザー定義関数は、"非決定的" とマークされます。|Low|  
|XML の union 型と list 型は、完全にはサポートされていません。|union 型と list 型は、完全にサポートされています (次の機能を含む)。<br /><br /> リストの和集合<br /><br /> 和集合の和集合<br /><br /> アトミック型のリスト<br /><br /> 和集合のリスト|Low|  
|xQuery メソッドに必要な SET オプションは、メソッドがビューまたはインライン テーブル値関数に含まれる場合に検証されません。|xQuery メソッドに必要な SET オプションは、メソッドがビューまたはインライン テーブル値関数に含まれる場合に検証されます。 メソッドの SET オプションが正しく設定されていない場合は、エラーが発生します。|Low|  
|行末文字 (復帰と改行) を含む XML 属性値は、XML 標準に従って正規化されません。 つまり、1 つの改行文字ではなく両方の文字が返されます。|行末文字 (復帰と改行) を含む XML 属性値は、XML 標準に従って正規化されます。 つまり、外部解析エンティティ (ドキュメント エンティティを含む) のすべての改行が、入力時に正規化されます。このとき、2 文字のシーケンス #xD #xA と、後ろに #xA がない #xD の両方について、1 つの #xA 文字に変換されます。<br /><br /> 行末文字を含む文字列値を転送するための属性を使用しているアプリケーションは、このような文字が送信されても受け取りません。 正規化処理を回避するには、XML 数字エンティティを使用してすべての行末文字をエンコードしてください。|Low|  
|列プロパティ ROWGUIDCOL および IDENTITY は、制約として不適切に指定できます。 たとえば、ステートメント `CREATE TABLE T (C1 int CONSTRAINT MyConstraint IDENTITY)` は実行されますが、制約名は保持されず、ユーザーはその制約にアクセスできません。|列プロパティ ROWGUIDCOL および IDENTITY は、制約として指定できません。 156 のエラーが返されます。|低|  
|などの双方向の代入を使用して、列を更新する`UPDATE T1 SET @v = column_name = <expression>`変数の有効期限の値は、ステートメントの開始値の代わりにステートメントの実行時など、WHERE 句や ON は、他の句で使用できるため、予期しない結果を生成できます. これにより、述語の意味が行ごとに予期せず変化することがあります。<br /><br /> この動作は、互換性レベルが 90 に設定されている場合にのみ適用されます。|双方向の代入を使用して列を更新すると、予想どおりの結果が生じます。これは、ステートメントの実行時に、列のステートメントの開始値のみが利用されるためです。|Low|  
|後述の「例」の例 E を参照してください。|後述の「例」の例 F を参照してください。|Low|  
|ODBC 関数 {fn CONVERT()} では、言語の既定の日付形式が使用されます。 言語によっては、既定の形式が YDM の場合があります。この場合、CONVERT() を {fn CURDATE()} などの YMD 形式が想定されている他の関数と組み合わせて使用すると、変換エラーが発生する可能性があります。|ODBC 関数 {fn CONVERT()} では、ODBC データ型 SQL_TIMESTAMP、SQL_DATE、SQL_TIME、SQLDATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP への変換時にスタイル 121 (言語に依存しない YMD 形式) が使用されます。|Low|  
|DATEPART などの datetime 組み込み関数では、文字列入力値が有効な datetime リテラルである必要はありません。 たとえば、SELECT DATEPART (year, '2007/05-30') が正常にコンパイルされます。|DATEPART などの datetime 組み込み関数では、文字列入力値が有効な datetime リテラルである必要があります。 無効な datetime リテラルを使用すると、エラー 241 が返されます。|Low|  
  
## <a name="reserved-keywords"></a>予約済みキーワード  
 互換性設定では、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で予約されているキーワードも判別されます。 次の表は、各互換性レベルで使用される予約済みキーワードです。  
  
|互換性レベル設定|予約済みキーワード|  
|----------------------------------|-----------------------|  
|130|未定。|  
|120|[なし] :|  
|110|WITHIN GROUP、TRY_CONVERT、SEMANTICKEYPHRASETABLE、SEMANTICSIMILARITYDETAILSTABLE、SEMANTICSIMILARITYTABLE|  
|100|CUBE、MERGE、ROLLUP|  
|90|EXTERNAL、PIVOT、UNPIVOT、REVERT、TABLESAMPLE|  
  
 各互換性レベルの予約済みキーワードには、そのレベル以下で導入されるキーワードもすべて含まれています。 したがって、たとえばレベル 110 のアプリケーションの場合、上の表に一覧表示されているすべてのキーワードが予約されています。 それより下位の互換性レベルでは、レベル 100 のキーワードは有効なオブジェクト名ですが、そのキーワードに対応するレベル 110 の言語機能は使用できません。  
  
 キーワードはいったん導入されると、キーワードの予約が維持されます。 たとえば、互換性レベル 90 で導入された予約済みキーワード PIVOT は、レベル 100、110、および 120 でも予約済みとして扱われます。  
  
 互換性レベル設定でキーワードとして予約した識別子をアプリケーションで使用しようとすると、アプリケーションは失敗します。 この問題を回避するいずれかの角かっこの間の識別子を囲む (**:operator[]**) または引用符 (**""**) ですたとえば、識別子を使用するアプリケーションをアップグレードする**外部。**互換性レベル 90 では、するには、いずれかに識別子を変更する可能性があります**[外部]**または**"EXTERNAL"**です。  
  
 詳細については、「[予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-compatibility-level"></a>A. 互換性レベルを変更する  
 次の例の互換性レベルを変更する、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースを`110,`[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 110;  
GO  
```  
  
 次の例では、現在のデータベースの互換性レベルを返します。  
  
```tsql  
SELECT name, compatibility_level   
FROM sys.databases   
WHERE name = db_name();  
```  
  
### <a name="b-ignoring--the-set-language-statement-except-under-compatibility-level-120"></a>B. 互換性レベル 120 を除く、SET LANGUAGE ステートメントは無視されます。  
 次のクエリでは、互換性レベル 120 を除く、SET LANGUAGE ステートメントは無視されます。  
  
```tsql  
SET DATEFORMAT dmy;   
DECLARE @t2 date = '12/5/2011' ;  
SET LANGUAGE dutch;   
SELECT CONVERT(varchar(11), @t2, 106);   
  
-- Results when the compatibility level is less than 120.   
12 May 2011   
  
-- Results when the compatibility level is set to 120).  
12 mei 2011  
```  
  
### <a name="c"></a>C.  
 互換性レベル設定 110 以下では、EXCEPT 句の右側にある再帰参照は、無限ループを作成します。  
  
```tsql  
WITH   
cte AS (SELECT * FROM (VALUES (1),(2),(3)) v (a)),  
r   
AS (SELECT a FROM Table1  
UNION ALL  
(SELECT a FROM Table1 EXCEPT SELECT a FROM r) )   
SELECT a   
FROM r;  
  
```  
  
### <a name="d"></a>D.  
 この例では、スタイル 0 と 121 の違いを示します。 日付と時刻のスタイルの詳細については、次を参照してください。 [CAST および CONVERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
```tsql  
CREATE TABLE t1 (c1 time(7), c2 datetime2);   
  
INSERT t1 (c1,c2) VALUES (GETDATE(), GETDATE());  
  
SELECT CONVERT(nvarchar(16),c1,0) AS TimeStyle0  
       ,CONVERT(nvarchar(16),c1,121)AS TimeStyle121  
       ,CONVERT(nvarchar(32),c2,0) AS Datetime2Style0  
       ,CONVERT(nvarchar(32),c2,121)AS Datetime2Style121  
FROM t1;  
  
-- Returns values such as the following.  
TimeStyle0       TimeStyle121       
Datetime2Style0      Datetime2Style121  
---------------- ----------------   
-------------------- --------------------------  
3:15PM           15:15:35.8100000   
Jun  7 2011  3:15PM  2011-06-07 15:15:35.8130000  
```  
  
### <a name="e"></a>E.  
 変数代入は、最上位レベルの UNION 演算子を含むステートメントで許可されていますが、予期しない結果が返されます。 たとえば、次のステートメントでは、ローカル変数で`@v`列の値が割り当てられている`BusinessEntityID`2 つのテーブルの和集合からです。 定義上、SELECT ステートメントが複数の値を返した場合は、最後に返された値が変数に割り当てられます。 この場合は、最後の値が変数に正しく割り当てられますが、SELECT UNION ステートメントの結果セットも返されます。  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET compatibility_level = 90;  
GO  
USE AdventureWorks2012;  
GO  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM HumanResources.Employee  
UNION ALL  
SELECT @v = BusinessEntityID FROM HumanResources.EmployeeAddress;  
SELECT @v;  
```  
  
### <a name="f"></a>F.  
 変数代入は、最上位レベルの UNION 演算子を含むステートメントでは許可されていません。 10734 のエラーが返されます。 エラーを解決するには、次の例で示すようにクエリを書き直してください。  
  
```tsql  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM   
    (SELECT BusinessEntityID FROM HumanResources.Employee  
     UNION ALL  
     SELECT BusinessEntityID FROM HumanResources.EmployeeAddress) AS Test;  
SELECT @v;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
 [データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) 
  
