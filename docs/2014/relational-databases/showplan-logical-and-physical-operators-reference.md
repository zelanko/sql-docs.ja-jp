---
title: プラン表示の論理操作と物理操作のリファレンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.showplan.nestedloops.f1
- sql12.swb.showplan.dynamic.f1
- sql12.swb.showplan.tableinsert.f1
- sql12.swb.showplan.remoteinsert.f1
- sql12.swb.showplan.lazyspool.f1
- sql12.swb.showplan.RIDLookup
- sql12.swb.showplan.hashmatchteam.f1
- sql12.swb.showplan.tablespool.f1
- sql12.swb.showplan.print.f1
- sql12.swb.showplan.clusteredindexupdate.f1
- sql12.swb.showplan.assert.f1
- sql12.swb.showplan.columnstoreindexscan.f1
- sql12.swb.showplan.tablevaluedfunction.f1
- sql12.swb.showplan.split.f1
- sql12.swb.showplan.union.f1
- sql12.swb.showplan.clusteredindexseek.f1
- sql12.swb.showplan.indexspool.f1
- sql12.swb.showplan.indexinsert.f1
- sql12.swb.showplan.clusteredindexscan.f1
- sql12.swb.showplan.buildhash.f1
- sql12.swb.showplan.clusteredindexmerge.f1
- sql12.swb.showplan.sequence.f1
- sql12.swb.showplan.hashmatchroot.f1
- sql12.swb.showplan.columnstoreindexupdate.f1
- sql12.swb.showplan.rightsemijoin.f1
- sql12.swb.showplan.fetchquery.f1
- sql12.swb.showplan.distinct.f1
- sql12.swb.showplan.hashmatch.f1
- sql12.swb.showplan.segment.f1
- sql12.swb.showplan.top.f1
- sql12.swb.showplan.columnstoreindexdelete.f1
- sql12.swb.showplan.gatherstreams.f1
- sql12.swb.showplan.remotedelete.f1
- sql12.swb.showplan.insert.f1
- sql12.swb.showplan.declare.f1
- sql12.swb.showplan.snapshot.f1
- sql12.swb.showplan.assign.f1
- sql12.swb.showplan.intrinsic.f1
- sql12.swb.showplan.mergejoin.f1
- sql12.swb.showplan.concatenation.f1
- sql12.swb.showplan.rowcountspool.f1
- sql12.swb.showplan.parametertablescan.f1
- sql12.swb.showplan.indexscan.f1
- sql12.swb.showplan.while.f1
- sql12.swb.showplan.columnstoreindexinsert.f1
- sql12.swb.showplan.tablemerge.f1
- sql12.swb.showplan.spool.f1
- sql12.swb.showplan.streamaggregate.f1
- sql12.swb.showplan.update.f1
- sql12.swb.showplan.innerjoin.f1
- sql12.swb.showplan.flowdistinct.f1
- sql12.swb.showplan.tableupdate.f1
- sql12.swb.showplan.result.f1
- sql12.swb.showplan.bitmap.f1
- sql12.swb.showplan.remoteindexseek.f1
- sql12.swb.showplan.populationquery.f1
- sql12.swb.showplan.rightouterjoin.f1
- sql12.swb.showplan.columnstoreindexmerge.f1
- sql12.swb.showplan.remotescan.f1
- sql12.swb.showplan.remoteupdate.f1
- sql12.swb.showplan.keyset.f1
- sql12.swb.showplan.collapse.f1
- sql12.swb.showplan.arithmeticexpression.f1
- sql12.swb.showplan.clusteredindexinsert.f1
- sql12.swb.showplan.computescalar
- sql12.swb.showplan.sort.f1
- sql12.swb.showplan.locate.f1
- sql12.swb.showplan.constantscan.f1
- sql12.swb.showplan.computescalar.f1
- sql12.swb.showplan.indexseek.f1
- sql12.swb.showplan.leftsemijoin.f1
- sql12.swb.showplan.leftantisemijoin.f1
- sql12.swb.showplan.fullouterjoin.f1
- sql12.swb.showplan.filter.f1
- sql12.swb.showplan.indexdelete.f1
- sql12.swb.showplan.repartitionstreams.f1
- sql12.swb.showplan.crossjoin.f1
- sql12.swb.showplan.mergeinterval.f1
- sql12.swb.showplan.bookmarklookup.f1
- sql12.swb.showplan.convert.f1
- sql12.swb.showplan.refreshquery.f1
- sql12.swb.showplan.distinctsort.f1
- sql12.swb.showplan.leftouterjoin.f1
- sql12.swb.showplan.rightantisemijoin.f1
- sql12.swb.showplan.deletedscan.f1
- sql12.swb.showplan.udx.f1
- sql12.swb.showplan.broadcast.f1
- sql12.swb.showplan.delete.f1
- sql12.swb.showplan.aggregate.f1
- sql12.swb.showplan.setfunction.f1
- sql12.swb.showplan.switch.f1
- sql12.swb.showplan.remoteindexscan.f1
- sql12.swb.showplan.eagerspool.f1
- sql12.swb.showplan.indexupdate.f1
- sql12.swb.showplan.keylookup.f1
- sql12.swb.showplan.branchrepartition.f1
- sql12.swb.showplan.rank.f1
- sql12.swb.showplan.tablescan.f1
- sql12.swb.showplan.distributestreams.f1
- sql12.swb.showplan.logrowscan.f1
- sql12.swb.showplan.parallelism.f1
- sql12.swb.showplan.bitmapcreate.f1
- sql12.swb.showplan.insertedscan.f1
- sql12.swb.showplan.tabledelete.f1
- sql12.swb.showplan.clusteredindexdelete.f1
- sql12.swb.showplan.remotequery.f1
- sql12.swb.showplan.if.f1
- sql12.swb.showplan.cache.f1
- sql12.swb.showplan.partialaggregate.f1
- sql12.swb.showplan.sql.f1
helpviewer_keywords:
- execution plans [SQL Server], operators
- ActualRows attribute
- reading execution plan output
- ActualRewinds attribute
- ActualEndOfScans attribute
- query tuning [SQL Server]
- mapping operators [SQL Server]
- operators [Database Engine query tuning]
- logical operators [SQL Server], execution plans
- logical operators [SQL Server], listed
- physical operators [SQL Server]
- ActualRebinds attribute
- execution plans [SQL Server], reading output
ms.assetid: e43fd0fe-5ea7-4ffe-8d52-759ef6a7c361
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e4e45de57f4ea1ea88b72df7190e5ec8c3a1f768
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62627735"
---
# <a name="showplan-logical-and-physical-operators-reference"></a>プラン表示の論理操作と物理操作のリファレンス
  操作は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でクエリやデータ操作言語 (DML) ステートメントを実行する方法を示します。 クエリ オプティマイザーでは、操作を使用して、クエリで指定された結果を作成するクエリ プラン、または DML ステートメントで指定された操作を実行するクエリ プランが構築されます。 クエリ プランは、物理操作をツリー構成で表現したものです。 クエリ プランを表示するには、SET SHOWPLAN ステートメント、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のグラフィカル実行プラン オプション、または SQL Server Profiler Showplan イベント クラスを使用します。  
  
 操作は、論理操作と物理操作に分類されます。  
  
 **論理演算子**  
 論理操作は、ステートメントの処理に使用される関係代数操作を表します。 つまり、論理操作は、どのような操作を実行する必要があるかを、概念的に示します。  
  
 **物理操作**  
 物理操作では、論理操作によって示される操作が実装されます。 それぞれの物理操作は、操作を実行するオブジェクトまたはルーチンです。 たとえば、一部の物理操作は、テーブル、インデックス、またはビューから、列や行にアクセスします。 他の物理操作は、計算、集計、データ整合性チェック、結合などの他の操作を実行します。 物理操作には、それぞれ関連するコストがかかります。  
  
 物理操作では、初期化、データの収集が行われた後に終了されます。 具体的には、物理操作は次の 3 つのメソッド呼び出しに応答できます。  
  
-   **Init()** : **Init()** メソッドは、物理操作自体を初期化し、必要なデータ構造を設定します。 通常、物理操作が受け取る **Init()** 呼び出しは 1 つだけですが、多くの Init() 呼び出しを受け取る場合もあります。  
  
-   **GetNext()** : **GetNext()** メソッドにより、物理操作がデータの最初の行または後続の行を取得します。 物理操作が受け取る **GetNext()** 呼び出しは、多数の場合もゼロの場合もあります。  
  
-   **Close()** : **Close()** メソッドにより、物理操作はクリーンアップ操作を実行し、物理操作自体がシャットダウンされます。 物理操作は、 **Close()** 呼び出しを 1 つだけ受け取ります。  
  
 **GetNext()** メソッドは、データ行を 1 行返します。このメソッドが呼び出された回数は、SET STATISTICS PROFILE ON または SET STATISTICS XML ON を使用して生成されるプラン表示出力で **ActualRows** として表示されます。 これらの SET オプションの詳細については、「[SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql)」および「[SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)」を参照してください。  
  
 プラン表示出力に表示される **ActualRebinds** および **ActualRewinds** の数は、**Init()** メソッドが呼び出された回数を示します。 ループ結合内部での操作でなければ、 **ActualRebinds** は 1、 **ActualRewinds** は 0 になります。 ループ結合内部での操作の場合、再バインドと巻き戻しの合計数は、結合外部で処理された行数に等しくなる必要があります。 再バインドとは、結合の変更された相関パラメーターと、内側部分の相関パラメーターの 1 つ以上を再評価する必要があることを意味します。 巻き戻しとは、変更された相関パラメーターを使用せず、前の内部の結果セットを再利用することを意味します。  
  
 **ActualRebinds** および **ActualRewinds** は、SET STATISTICS XML ON を使用して生成された XML プラン表示出力に存在します。 これらの値は、**非クラスター化インデックススプール**、 `Remote Query`、**行カウントスプール**、 `Sort`、**テーブルスプール**、および**テーブル値関数**の各演算子に対してのみ設定されます。 また、 **Startupexpression**属性が TRUE に設定され`Assert`ている場合は、と**フィルター**演算子に対して**actualrebinds バインド**と**actualrebinds 戻し**を設定することもできます。  
  
 **ActualRebinds** および **ActualRewinds** が XML プラン表示に存在する場合、これらの値が **EstimateRebinds** および **EstimateRewinds**に相当します。 存在しない場合、予測行数 (**EstimateRows**) が実際の行数 (**ActualRows**) に相当します。 この場合、実際のグラフィカルなプラン表示出力では、実際の再バインド数と実際の巻き戻し数としてゼロが表示されることに注意してください。  
  
 関連するカウンター **ActualEndOfScans**は、プラン表示出力が SET STATISTICS XML ON を使用して生成されている場合のみ使用できます。 物理操作がデータ ストリームの最後に達するたびに、このカウンターの値は 1 ずつ増加します。 物理操作がデータ ストリームの最後に達することのできる回数は、0 回、1 回、あるいは複数回です。 再バインドおよび巻き戻しと同様に、スキャンの終了回数は、ループ結合内部での操作の場合のみ 2 回以上になります。 スキャンの終了回数は、再バインドおよび巻き戻しの合計数以下になる必要があります。  
  
## <a name="mapping-physical-and-logical-operators"></a>物理操作と論理操作の対応関係  
 クエリ オプティマイザーでは、ツリー構成の論理操作としてクエリ プランが作成されます。 クエリ オプティマイザーでは、プランが作成されると、各論理操作にとって最も効率的な物理操作が選択されます。 クエリ オプティマイザーでは、論理操作をどの物理操作から実装するかを判断するために、コストベースの手法が使用されます。  
  
 通常、複数の物理操作で 1 つの論理操作を実装できます。 ただし、めったにないケースですが、1 つの物理操作で複数の論理操作を実装することもできます。  
  
## <a name="operator-descriptions"></a>操作の説明  
 このセクションには、論理演算子と物理演算子の説明が含まれています。  
  
|グラフィカルな実行プランのアイコン|プラン表示操作|説明|  
|-----------------------------------|-----------------------|-----------------|  
|なし|`Aggregate`|`Aggregate` 操作は、MIN、MAX、SUM、COUNT、AVG のいずれかが含まれた式を計算します。 `Aggregate` は、論理操作または物理操作です。|  
|![Arithmetic Expression 操作アイコン](../../2014/database-engine/media/arithmetic-expression-32x-2.gif "Arithmetic Expression 操作アイコン")|`Arithmetic Expression`|`Arithmetic Expression` 操作は、行の既存の値から新しい値を計算します。 `Arithmetic Expression` は [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では使用されません。|  
|![Assert 操作アイコン](../../2014/database-engine/media/assert-32x.gif "Assert 操作アイコン")|`Assert`|`Assert` 操作は、状態の検証を行います。 たとえば、参照整合性の検証や、スカラー サブクエリによって 1 行返されることの確認を行います。 演算子は`Assert` 、各入力行に対して、実行プラン`Argument`の列の式を評価します。 この式が NULL であると評価されると、行は `Assert` 操作を通過して、クエリの実行が継続されます。 式が NULL 以外の値に評価されると、相応のエラーが発生します。 `Assert` 操作は物理操作です。|  
|![Assign 言語要素アイコン](../../2014/database-engine/media/assign-32.gif "Assign 言語要素アイコン")|`Assign`|`Assign` 操作は、変数に式の値または定数値を代入します。 `Assign` は言語要素です。|  
|None|`Asnyc Concat`|`Asnyc Concat` 操作は、リモート クエリ (分散クエリ) でのみ使用されます。 Async Concat には *n* 個の子ノードと 1 個の親ノードが含まれます。 通常、子ノードのいくつかはリモート コンピューターで、分散クエリに参加しています。 `Asnyc Concat` は、すべての子ノードに同時に `open()` 呼び出しを行い、各子ノードにビットマップを適用します。 `Async Concat` では、1 に設定されているビットごとに、要求時に出力行が親ノードに送信されます。|  
|![Bitmap 操作アイコン](../../2014/database-engine/media/bitmap-32x.gif "Bitmap 操作アイコン")|`Bitmap`|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]演算子を`Bitmap`使用して、並列クエリプランでビットマップフィルターを実装します。 ビットマップフィルターは、 `Parallelism`演算子などの別の演算子を使用して行を渡す前に、結合レコードを生成できないキー値を持つ行を削除することで、クエリの実行を高速化します。 ビットマップ フィルターは、操作ツリーの特定の部分にあるテーブルから得られた一連の値の圧縮表現を使用して、同じツリーの別の部分にある 2 つ目のテーブルから行を抽出します。 不要な行をクエリの初期段階で排除することにより、それ以降の操作に渡される行数が減り、その結果、クエリの全体的なパフォーマンスが向上します。 オプティマイザーは、どのような場合にビットマップの選択度が効果を期待できる程度に高くなるか、また、どのような操作にフィルターを適用すべきかを判断します。 `Bitmap` は物理操作です。|  
|![Bitmap 操作アイコン](../../2014/database-engine/media/bitmap-32x.gif "Bitmap 操作アイコン")|`Bitmap Create`|`Bitmap Create` 操作は、ビットマップが作成されるプラン表示の出力に使用されます。 `Bitmap Create` は論理操作です。|  
|![Bookmark Lookup 操作アイコン](../../2014/database-engine/media/bookmark-lookup-32x.gif "Bookmark Lookup 操作アイコン")|`Bookmark Lookup`|`Bookmark Lookup` 操作は、ブックマーク (行 ID またはクラスター化キー) を使用してテーブルまたはクラスター化インデックスの対応行を参照します。 列`Argument`には、テーブルまたはクラスター化インデックスの行を検索するために使用されるブックマークラベルが含まれています。 `Argument`列には、行が検索されるテーブルまたはクラスター化インデックスの名前も含まれます。 `Argument`列に WITH プリフェッチ句が含まれている場合、クエリプロセッサは、テーブルまたはクラスター化インデックスでブックマークを検索するときに、非同期プリフェッチ (先読み) を使用するのが最適であると判断しました。<br /><br /> `Bookmark Lookup` は [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では使用されません。 代わりに、`Clustered Index Seek` および `RID Lookup` によってブックマーク参照機能が提供されます。 `Key Lookup` 操作でもこの機能が提供されます。|  
|None|`Branch Repartition`|並列クエリ プランでは、反復子に概念上の領域が存在する場合があります。 このような領域内にある反復子はすべて、並列スレッドにより実行できます。 領域自体は、順次実行される必要があります。 個別の領域内の `Parallelism` 反復子のいくつかは、`Branch Repartition` と呼ばれます。 このような 2 つの領域間の境界にある `Parallelism` 反復子は、`Segment Repartition` と呼ばれます。 `Branch Repartition` と `Segment Repartition` は論理操作です。|  
|None|`Broadcast`|`Broadcast`には、1つの子ノードと*n 個*の親ノードがあります。 `Broadcast` では、要求時に複数のコンシューマーに入力行が送信されます。 各コンシューマーがすべての行を取得します。 たとえば、すべてのコンシューマーがハッシュ結合のビルド側の場合、ハッシュ テーブルの *n* 個のコピーがビルドされます。|  
|![Build Hash 操作アイコン](../../2014/database-engine/media/build-hash.gif "Build Hash 操作アイコン")|`Build Hash`|xVelocity メモリ最適化列ストア インデックスのバッチ ハッシュ テーブルの作成を示します。|  
|None|`Cache`|`Cache`は、 **Spool**操作の特殊なバージョンです。 データは 1 行分しか格納されません。 `Cache` は論理操作です。 `Cache` は [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では使用されません。|  
|![Clustered Index Delete 操作アイコン](../../2014/database-engine/media/clustered-index-delete-32x.gif "Clustered Index Delete 操作アイコン")|`Clustered Index Delete`|`Clustered Index Delete` 操作は、クエリ実行プランの Argument 列 (引数) で指定されているクラスター化インデックスから行を削除します。 Argument 列に WHERE:() 述語がある場合、その述語に適合する行だけが削除されます。`Clustered Index Delete`  は物理操作です。|  
|![Clustered Index Insert 操作アイコン](../../2014/database-engine/media/clustered-index-insert-32x.gif "Clustered Index Insert 操作アイコン")|`Clustered Index Insert`|`Clustered Index Insert` プラン表示操作では、Argument 列で指定されているクラスター化インデックスに、入力からの行が挿入されます。 また、Argument 列には、各列に設定する値を示す SET:() 述語も含まれます。 に`Clustered Index Insert`挿入値の子がない場合、挿入された行は`Insert`演算子自体から取得されます。`Clustered Index Insert`  は物理操作です。|  
|![Clustered Index Merge 操作アイコン](../../2014/database-engine/media/clustered-index-merge-32x.gif "Clustered Index Merge 操作アイコン")|**Clustered Index Merge**|**Clustered Index Merge** 操作は、マージ データ ストリームをクラスター化インデックスに適用します。 操作は、演算子の`Argument`列に指定されているクラスター化インデックスから行を削除、更新、または挿入します。 実際に実行される操作は、演算子の`Argument`列に指定された**アクション**列のランタイム値によって異なります。 **Clustered Index Merge** は物理操作です。|  
|![Clustered Index Scan 操作アイコン](../../2014/database-engine/media/clustered-index-scan-32x.gif "Clustered Index Scan 操作アイコン")|`Clustered Index Scan`|`Clustered Index Scan` 操作は、クエリ実行プランの Argument 列 (引数) に指定されたクラスター化インデックスをスキャンします。 オプションの WHERE:() 述語がある場合、この述語に適合する行だけが返されます。 Argument 列 (引数) に ORDERED 句が含まれている場合は、クラスター化インデックスの並べ替え順での行出力が要求されています。 ORDERED 句がない場合は、ストレージ エンジンが最適な方法でインデックスをスキャンします。出力の並べ替えは必ずしも行われません。 `Clustered Index Scan` は論理操作でもあり、物理操作でもあります。|  
|![Clustered Index Seek 操作アイコン](../../2014/database-engine/media/clustered-index-seek-32x.gif "Clustered Index Seek 操作アイコン")|`Clustered Index Seek`|`Clustered Index Seek` 操作は、インデックスのシーク機能を使用してクラスター化インデックスから行を取得します。 列`Argument`には、使用されているクラスター化インデックスの名前と SEEK:() 述語が含まれています。 ストレージ エンジンはインデックスを使用して、この SEEK:() 述語に適合する行だけを処理します。 また、WHERE:() 述語を含めることもできます。この場合、ストレージ エンジンは、SEEK:() 述語に適合するすべての行が WHERE:() 述語に適合するかどうかを評価します。ただし、WHERE:() 述語は省略可能であり、処理を行うときにインデックスを使用しません。<br /><br /> 列に`Argument` ORDERED 句が含まれている場合、クエリプロセッサは、クラスター化インデックスが並べ替えられた順序で行を返す必要があると判断しました。 ORDERED 句がない場合、ストレージ エンジンが最適な方法でインデックスを検索します。ただし、出力が並べ替えられるとは限りません。 出力で行の順序を保持する場合、並べ替えられていない出力に比べて効率が低下することがあります。 LOOKUP キーワードを指定すると、ブックマーク参照が行われます。 以降[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]のバージョンでは、 `Key Lookup`演算子によってブックマーク参照機能が提供されます。 `Clustered Index Seek` は論理操作でもあり、物理操作でもあります。|  
|![Clustered Index Update 操作アイコン](../../2014/database-engine/media/clustered-index-update-32x.gif "Clustered Index Update 操作アイコン")|`Clustered Index Update`|操作`Clustered Index Update`は、 `Argument`列に指定されているクラスター化インデックスの入力行を更新します。WHERE:() 述語がある場合、この述語に適合する行だけが更新されます。 SET:() 述語がある場合、更新される各列がこの値に設定されます。 DEFINE:() 述語がある場合、この操作によって定義される値が一覧表示されます。 これらの値は、SET 句、またはこの操作内かこのクエリ内で参照されることがあります。 `Clustered Index Update` は論理操作でもあり、物理操作でもあります。|  
|![Collapse 操作アイコン](../../2014/database-engine/media/collapse-32x.gif "Collapse 操作アイコン")|`Collapse`|`Collapse` 操作により、更新処理が最適化されます。 更新が実行されると、(`Split` 操作を使用して) 削除と挿入に分割されます。 列`Argument`には、キー列の一覧を指定する GROUP BY:() 句が含まれています。 クエリ プロセッサでは、同じキー値を削除して挿入する操作が隣接する行で検出されると、これらの個別の操作を 1 つのより効率的な更新操作に置き換えます。 `Collapse` は論理操作でもあり、物理操作でもあります。|  
|![Columnstore インデックス スキャン](../../2014/database-engine/media/columnstoreindexscan.gif "Columnstore インデックス スキャン")|`Columnstore Index Scan`|操作`Columnstore Index Scan`は、クエリ実行プランの`Argument`列に指定されている列ストアインデックスをスキャンします。|  
|![Compute Scalar 操作アイコン](../../2014/database-engine/media/compute-scalar-32x.gif "Compute Scalar 操作アイコン")|`Compute Scalar`|演算子`Compute Scalar`は、式を評価して、計算されたスカラー値を生成します。 この値は、ユーザー、クエリの参照先、またはその両方に返されることがあります。 両方に返される例としては、フィルター述語や結合述語があります。 `Compute Scalar` は論理操作でもあり、物理操作でもあります。<br /><br /> `Compute Scalar`SET STATISTICS XML によって生成されたプラン表示に表示`RunTimeInformation`される演算子には、要素が含まれていない場合があります。 **で**[実際の実行プランを含める] **オプションが選択されているときは、グラフィカルなプラン表示の**[プロパティ] **ウィンドウに** [実際の行数] **、** [実際の再バインド数] **、および** [実際の巻き戻し数] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]が表示されないことがあります。 その場合、コンパイルされたクエリ プランでは Compute Scalar 操作が使用されていたのに、実行時のクエリ プランではこの操作の作業が別の操作によって行われたことを意味します。 また、SET STATISTICS PROFILE によって生成されるプラン表示出力の実行の数は、SET STATISTICS XML によって生成されるプラン表示の再バインドと巻き戻しの合計と同じになります。|  
|![Concatenation 操作アイコン](../../2014/database-engine/media/concatenation-32x.gif "Concatenation 操作アイコン")|**組み合わせ**|**Concatenation** 操作は複数の入力をスキャンし、スキャンした各行を返します。 **Concatenation** は、主に [!INCLUDE[tsql](../includes/tsql-md.md)] UNION ALL コンストラクトの実装に使用します。 **Concatenation** 物理操作は入力が複数で出力が 1 つです。 この操作では、最初の入力ストリームの行が出力ストリームにコピーされ、同じ動作が以降の各入力ストリームに対して行われます。 **Concatenation** は論理操作でもあり、物理操作でもあります。|  
|![Constant Scan 操作アイコン](../../2014/database-engine/media/constant-scan-32x.gif "Constant Scan 操作アイコン")|`Constant Scan`|演算子`Constant Scan`は、1つ以上の定数行をクエリに導入します。 `Compute Scalar`演算子は、 `Constant Scan`演算子によって生成された行に列を追加するために、の`Constant Scan`後に使用されることがよくあります。|  
|![Convert (データベース エンジン) 言語要素アイコン](../../2014/database-engine/media/convert-32x.gif "Convert (データベース エンジン) 言語要素アイコン")|`Convert`|`Convert` 操作は、スカラー データ型間の変換を行います。 `Convert` は言語要素です。|  
|None|`Cross Join`|`Cross Join` 操作は、最初 (上部) の入力の各行と 2 番目 (下部) の入力の各行を結合します。 `Cross Join` は論理操作です。|  
|![Cursor Catchall カーソル操作アイコン](../../2014/database-engine/media/cursor-catch-all.gif "Cursor Catchall カーソル操作アイコン")|`catchall`|汎用アイコンは、グラフィカルなプラン表示を生成するロジックで、反復子に適したアイコンが見つからない場合に表示されます。 汎用アイコンは、必ずしもエラー状態を示しているわけではありません。 汎用アイコンには、青 (反復子)、オレンジ (カーソル)、緑 ( [!INCLUDE[tsql](../includes/tsql-md.md)] 言語要素) の 3 種類があります。|  
|None|**カーソル**|**カーソル** 論理操作および物理操作は、カーソル操作に関するクエリまたは更新処理がどのように実行されたかを示すために使用されます。 カーソル物理操作は、キーセット ドリブン カーソルの使用など、カーソルの処理に使用される物理的な実装アルゴリズムを示します。 カーソル実行の各ステップは、物理操作に関係します。 カーソル論理操作は、カーソルが読み取り専用であるなどの、カーソルのプロパティを示します。<br /><br /> 論理操作には、Asynchronous、Optimistic、Primary、Read Only、Scroll Locks、Secondary、および Synchronous があります。<br /><br /> 物理操作には、Dynamic、Fetch Query、Keyset、Population Query、Refresh Query、および Snapshot があります。|  
|![Declare 言語要素アイコン](../../2014/database-engine/media/declare-32x.gif "Declare 言語要素アイコン")|`Declare`|操作`Declare`は、クエリプランにローカル変数を割り当てます。 `Declare` は言語要素です。|  
|![Delete (データベース エンジン) 操作アイコン](../../2014/database-engine/media/delete-32x.gif "Delete (データベース エンジン) 操作アイコン")|`Delete`|操作`Delete`は、 `Argument`列のオプションの述語を満たすオブジェクト行からを削除します。|  
|![Delete Scan 操作アイコン](../../2014/database-engine/media/delete-scan-32x.gif "Delete Scan 操作アイコン")|`Deleted Scan`|`Deleted Scan` 操作は、削除されたテーブルをトリガー内でスキャンします。|  
|None|`Distinct`|`Distinct` 操作は、行セットや値のコレクションから重複部分を削除します。 `Distinct` は論理操作です。|  
|None|`Distinct Sort`|論理`Distinct Sort`操作は、入力をスキャンし、重複部分を削除し、 `Argument`列の DISTINCT ORDER by:() 述語に指定されている列で並べ替えます。 `Distinct Sort` は論理操作です。|  
|![Distribute Streams 並列処理操作アイコン](../../2014/database-engine/media/parallelism-distribute-stream.gif "Distribute Streams 並列処理操作アイコン")|**Distribute Streams**|**Distribute Streams** 操作は、並列クエリ プランのみで使用されます。 **Distribute Streams** 操作は、レコードの 1 つの入力ストリームを使用して複数の出力ストリームを生成します。 レコードの内容と形式は変更されません。 入力ストリームの各レコードは、出力ストリームのいずれかに含まれます。 この操作では、出力ストリーム内で入力レコードの相対順序が自動的に保持されます。 通常、特定の入力レコードが属する出力ストリームを判断するにはハッシュ操作が使用されます。<br /><br /> 出力がパーティション分割されている`Argument`場合、列にはパーティション列:() 述語とパーティション分割列が含まれます。 **Distribute Streams** は論理操作です。|  
|![Dynamic カーソル操作アイコン](../../2014/database-engine/media/dynamic-32x.gif "Dynamic カーソル操作アイコン")|`Dynamic`|`Dynamic` 操作は、他のユーザーによる変更をすべて表示できるカーソルを使用します。|  
|![Spool 操作アイコン](../../2014/database-engine/media/spool-32x.gif "Spool 操作アイコン")|**Eager Spool**|**一括スプール**操作は、入力全体を受け取り、データベースに格納されて`tempdb`いる非表示の一時オブジェクトに各行を格納します。 演算子が巻き戻し (たとえば、 `Nested Loops`演算子によって) されていても、再バインドが不要な場合は、入力を再スキャンする代わりにスプールされたデータが使用されます。 再バインドが必要な場合は、スプールされたデータが破棄され、(再バインドされる) 入力の再スキャンによりスプール オブジェクトが再構築されます。 **Eager Spool** 操作では、操作のスプール ファイルが "集中的" に構築されます。たとえば、スプールの親操作によって最初の行が要求されると、スプール操作によって入力操作からのすべての行が使用され、それらの行がスプールに格納されます。 **Eager Spool** は論理操作です。|  
|![Fetch Query カーソル操作アイコン](../../2014/database-engine/media/fetch-query-32x.gif "Fetch Query カーソル操作アイコン")|`Fetch Query`|`Fetch Query` 操作は、カーソルに対してフェッチが実行されたときに行を取得します。|  
|![Filter (データベース エンジン) 操作アイコン](../../2014/database-engine/media/filter-32x.gif "Filter (データベース エンジン) 操作アイコン")|**Assert**|**Filter**操作は、入力をスキャンし、 `Argument`列に表示されるフィルター式 (述語) に適合する行だけを返します。|  
|None|`Flow Distinct`|`Flow Distinct` 論理操作は入力をスキャンし、重複部分を削除します。 `Distinct`演算子は、出力を生成する前にすべての入力を使用しますが、 **flowdistinct**操作は、入力から取得された各行を返します (行が重複する場合は破棄されます)。|  
|なし|`Full Outer Join`|`Full Outer Join` 論理操作は、最初 (上部) の入力で結合述語に適合し、2 番目 (下部) の入力の各行と結合された各行を返します。 また、以下の行も返します。<br /><br /> - 2 番目の入力に一致する行がない最初の入力の行。<br /><br /> - 最初の入力に一致する行がない 2 番目の入力の行。<br /><br /> <br /><br /> 一致する値がない入力は NULL 値として返されます。 `Full Outer Join` は論理操作です。|  
|![Gather Streams 並列処理操作アイコン](../../2014/database-engine/media/parallelism-32x.gif "Gather Streams 並列処理操作アイコン")|**Gather Streams**|**Gather Streams** 操作は、並列クエリ プランでのみ使用されます。 **Gather Streams** 操作は複数の入力ストリームを使用し、入力ストリームを組み合わせてレコードの単一出力ストリームを作成します。 レコードの内容と形式は変更されません。 この操作で順序を保持する場合は、すべての入力ストリームが並べ替えられている必要があります。 出力が順序付けされて`Argument`いる場合、この列には ORDER BY:() 述語と順序付けされている列の名前が含まれます。 **Gather Streams** は論理操作です。|  
|![Hash Match 操作アイコン](../../2014/database-engine/media/hash-match-32x.gif "Hash Match 操作アイコン")|`Hash Match`|`Hash Match` 操作は、ビルド入力の行ごとにハッシュ値を計算してハッシュ テーブルを作成します。 ハッシュ値の作成に使用される列の一覧を含む HASH:() 述語が`Argument`列に表示されます。 次に、該当するプローブ行ごとに同じハッシュ関数を使用してハッシュ値が計算され、ハッシュ テーブル内で一致検索が行われます。 残余述語が存在する場合 ( `Argument`列の残余:() によって識別されます)、行が一致と見なされるためにもその述語が満たされている必要があります。 動作は、次に示すように、実行している論理操作によって異なります。<br /><br /> すべての結合では、最初 (上部) の入力を使用してハッシュ テーブルを作成し、2 番目 (下部) の入力を使用してハッシュ テーブルを探索します。 出力は、結合の種類で指定されているとおりに一致します (または一致しません)。 複数の結合が同じ結合列を使用する場合、これらの操作はハッシュ チームにグループ化されます。<br /><br /> Distinct 操作または Aggregate 操作の場合、入力を使用してハッシュ テーブルを作成します (重複部分を削除し、集計式を計算します)。 ハッシュ テーブルを作成したら、テーブルをスキャンしすべてのエントリを出力します。<br /><br /> Union 操作の場合、最初の入力を使用してハッシュ テーブルを作成します (重複部分は削除します)。 2 番目の入力 (重複部分はありません) を使用して、ハッシュ テーブルを探索して一致しないすべての行を返します。次に、ハッシュ テーブルをスキャンし、すべてのエントリを返します。<br /><br /> <br /><br /> `Hash Match` は物理操作です。|  
|![If 言語要素アイコン](../../2014/database-engine/media/if-32x.gif "If 言語要素アイコン")|`If`|`If` 操作では、式に基づく条件処理を実行します。 `If` は言語要素です。|  
|なし|`Inner Join`|`Inner Join` 論理操作は、最初 (上部) の入力と 2 番目 (下部) の入力の結合に適合する各行を返します。|  
|![Insert (データベース エンジン) 操作アイコン](../../2014/database-engine/media/insert-32x.gif "Insert (データベース エンジン) 操作アイコン")|`Insert`|論理`Insert`操作は、 `Argument`列に指定されたオブジェクトに入力から各行を挿入します。 物理操作は、`Table Insert` 操作、`Index Insert` 操作、または `Clustered Index Insert` 操作のいずれかです。|  
|![Inserted Scan 操作アイコン](../../2014/database-engine/media/inserted-scan-32x.gif "Inserted Scan 操作アイコン")|**Inserted Scan**|**Inserted Scan** 操作は、 **inserted** テーブルをスキャンします。 **Inserted Scan** 操作は論理操作でもあり、物理操作でもあります。|  
|![Intrinsic 言語要素アイコン](../../2014/database-engine/media/intrinsic-32x.gif "Intrinsic 言語要素アイコン")|`Intrinsic`|`Intrinsic` 操作では、内部 [!INCLUDE[tsql](../includes/tsql-md.md)] 関数が呼び出されます。 `Intrinsic` は言語要素です。|  
|![Iterator Catchall 操作アイコン](../../2014/database-engine/media/iterator-catch-all.gif "Iterator Catchall 操作アイコン")|`Iterator`|`Iterator` 汎用アイコンは、グラフィカルなプラン表示を生成するロジックで、反復子に適したアイコンが見つからない場合に表示されます。 汎用アイコンは、必ずしもエラー状態を示しているわけではありません。 汎用アイコンには、青 (反復子)、オレンジ (カーソル)、緑 ( [!INCLUDE[tsql](../includes/tsql-md.md)] 言語コンストラクト) の 3 種類があります。|  
|![Bookmark Lookup 操作アイコン](../../2014/database-engine/media/bookmark-lookup-32x.gif "Bookmark Lookup 操作アイコン")|`Key Lookup`|`Key Lookup`演算子は、クラスター化インデックスを持つテーブルのブックマーク参照です。 この`Argument`列には、クラスター化インデックスの名前と、クラスター化インデックスの行を検索するために使用されるクラスター化キーが含まれています。 `Key Lookup`常に`Nested Loops`演算子を伴います。 `Argument`列に WITH プリフェッチ句がある場合、クエリプロセッサは、クラスター化インデックスでブックマークを検索するときに、非同期プリフェッチ (先行読み取り) を使用することが最適であると判断しました。<br /><br /> クエリプランで演算子`Key Lookup`を使用することは、クエリがパフォーマンスチューニングの恩恵を受ける可能性があることを示しています。 たとえば、カバリング インデックスを追加することにより、クエリ パフォーマンスが向上する場合があります。|  
|![Keyset カーソル操作アイコン](../../2014/database-engine/media/keyset-32x.gif "Keyset カーソル操作アイコン")|`Keyset`|`Keyset` 操作では、カーソルを使用して更新内容を参照できます。ただし、他のユーザーが挿入した内容は参照できません。|  
|![言語要素の汎用アイコン](../../2014/database-engine/media/language-construct-catch-all.gif "言語要素の汎用アイコン")|`Language Element`|`Language Element` 汎用アイコンは、グラフィカルなプラン表示を生成するロジックで、反復子に適したアイコンが見つからない場合に表示されます。 汎用アイコンは、必ずしもエラー状態を示しているわけではありません。 汎用アイコンには、青 (反復子)、オレンジ (カーソル)、緑 ( [!INCLUDE[tsql](../includes/tsql-md.md)] 言語コンストラクト) の 3 種類があります。|  
|![Spool 操作アイコン](../../2014/database-engine/media/spool-32x.gif "Spool 操作アイコン")|**Lazy Spool**|**Lazy Spool**論理操作は、データベースに格納されて`tempdb`いる非表示の一時オブジェクトに入力から各行を格納します。 演算子が巻き戻し (たとえば、 `Nested Loops`演算子によって) されていても、再バインドが不要な場合は、入力を再スキャンする代わりにスプールされたデータが使用されます。 再バインドが必要な場合は、スプールされたデータが破棄され、(再バインドされる) 入力の再スキャンによりスプール オブジェクトが再構築されます。 **Lazy Spool** 操作のスプール ファイルは "レイジー" 手法で構築されます。つまり、1 回にすべての行を処理するのではなく、スプールの親操作から行が要求されるたびに入力操作から行を取得し、その行をスプールに格納します。 Lazy Spool は論理操作です。|  
|なし|`Left Anti Semi Join`|`Left Anti Semi Join` 操作は、最初 (上部) の入力の中に 2 番目 (下部) の入力に一致する行がない場合に該当する行を返します。 `Argument`列に結合述語が存在しない場合は、各行が一致する行になります。 `Left Anti Semi Join` は論理操作です。|  
|None|`Left Outer Join`|`Left Outer Join` 操作は、最初 (上部) の入力と 2 番目 (下部) の入力の結合に適合する各行を返します。 また、最初 (上部) の入力の中で 2 番目 (下部) の入力に一致する行がない行も返します。 2 番目の入力の一致しない行は NULL 値として返されます。 `Argument`列に結合述語が存在しない場合は、各行が一致する行になります。 `Left Outer Join` は論理操作です。|  
|None|`Left Semi Join`|`Left Semi Join` 操作は、最初 (上部) の入力の中に 2 番目 (下部) の入力に一致する行がある場合に該当する行を返します。 `Argument`列に結合述語が存在しない場合は、各行が一致する行になります。 `Left Semi Join` は論理操作です。|  
|![Log Row Scan 操作アイコン](../../2014/database-engine/media/log-row-scan-32x.gif "Log Row Scan 操作アイコン")|`Log Row Scan`|`Log Row Scan` 操作は、トランザクション ログをスキャンします。 `Log Row Scan` は論理操作でもあり、物理操作でもあります。|  
|![Merge Interval 操作アイコン](../../2014/database-engine/media/merge-interval-32x.gif "Merge Interval 操作アイコン")|`Merge Interval`|`Merge Interval` 操作は、重複している可能性のある複数の間隔をマージして、重複しない最小限の間隔を作成します。この間隔は、インデックス エントリのシークに使用されます。 通常、この演算子は、演算子を`Compute Scalar`介し`Constant Scan`て1つ以上の演算子の上に表示されます。この演算子は、この演算子がマージする間隔 (行内の列として表される) を構築します。 `Merge Interval` は論理操作でもあり、物理操作でもあります。|  
|![Merge Join 操作アイコン](../../2014/database-engine/media/merge-join-32x.gif "Merge Join 操作アイコン")|**マージ結合**|**Merge Join** 操作は Inner Join、Left Outer Join、Left Semi Join、Left Anti Semi Join、Right Outer Join、Right Semi Join、Right Anti Semi Join、Union の各論理操作を実行します。<br /><br /> この`Argument`列では、**マージ結合**演算子に merge:() 述語が含まれています。操作が一対多の結合を実行している場合、または操作が多対多の結合を実行している場合は多対多の merge:() 述語を含みます。 この`Argument`列には、操作の実行に使用される列のコンマ区切りの一覧も含まれています。 **Merge Join** 操作には、それぞれの列を基準に並べ替えられた 2 つの入力が必要です。この並べ替えを行うときは、クエリ プランに明示的な並べ替え操作を挿入することが可能です。 明示的な並べ替えが必要でない場合、Merge Join 操作は特に効果的です。たとえば、データベースに適切な B ツリー インデックスがある場合、またはマージ結合とロール アップを含むグループ化など、複数の操作で並べ替え順序を利用できる場合などです。 **Merge Join** は物理操作です。|  
|![Nested Loops 操作アイコン](../../2014/database-engine/media/nested-loops-32x.gif "Nested Loops 操作アイコン")|`Nested Loops`|`Nested Loops` 操作は、内部結合、左外部結合、左半結合、左反半結合の各論理操作を実行します。 ネステッド ループ結合では、外部テーブルの行ごとに内部テーブルが検索されます。検索には、通常はインデックスが使用されます。 クエリ プロセッサにより、予想コストに基づいて、内部入力でインデックスを検索する場所の絞り込みを向上するために、外部入力を並べ替えるかどうかが判断されます。 `Argument`列の (省略可能な) 述語を満たす行は、実行されている論理操作に基づいて、該当するものとして返されます。 `Nested Loops` は物理操作です。|  
|![Nonclustered Index Delete 操作アイコン](../../2014/database-engine/media/nonclust-index-delete-32x.gif "Nonclustered Index Delete 操作アイコン")|`Nonclustered Index Delete`|操作`Nonclustered Index Delete`は、 `Argument`列に指定された非クラスター化インデックスから入力行を削除します。 `Nonclustered Index Delete` は物理操作です。|  
|![Nonclustered Index Insert 操作アイコン](../../2014/database-engine/media/nonclust-index-insert-32x.gif "Nonclustered Index Insert 操作アイコン")|`Index Insert`|操作`Index Insert`は、 `Argument`列に指定された非クラスター化インデックスに、入力からの行を挿入します。 また、`Argument` 列には、各列に設定する値を示す SET:() 述語も含まれます。 `Index Insert` は物理操作です。|  
|![Nonclustered Index Scan 操作アイコン](../../2014/database-engine/media/nonclustered-index-scan-32x.gif "Nonclustered Index Scan 操作アイコン")|`Index Scan`|演算子`Index Scan`は、 `Argument`列に指定された非クラスター化インデックスからすべての行を取得します。 `Argument`列にオプションの WHERE:() 述語がある場合、その述語に適合する行だけが返されます。 `Index Scan` は論理操作でもあり、物理操作でもあります。|  
|![Nonclustered Index Seek 操作アイコン](../../2014/database-engine/media/index-seek-32x.gif "Nonclustered Index Seek 操作アイコン")|`Index Seek`|`Index Seek` 操作は、インデックスのシーク機能を使用して非クラスター化インデックスから行を取得します。 列`Argument`には、使用されている非クラスター化インデックスの名前が含まれます。 また、SEEK:() 述語も含まれます。 ストレージ エンジンはインデックスを使用して、SEEK:() 述語に適合する行だけを処理します。 必要に応じて、この列には WHERE:() 述語が含まれることがあります。この述語は、ストレージ エンジンによって SEEK:() 述語に適合するすべての行に対して評価されます (この処理を行うのにインデックスは使用されません)。 列に`Argument` ORDERED 句が含まれている場合、クエリプロセッサは、非クラスター化インデックスが並べ替えられた順序で行を返す必要があると判断しました。 ORDERED 句がない場合は、ストレージ エンジンにより、最適な方法でインデックスが検索されます (出力が並べ替えられるとは限りません)。 出力順序が保持されるようにすると、並べ替えずに出力する場合よりも効率が低下する可能性があります。 `Index Seek` は論理操作でもあり、物理操作でもあります。|  
|![Nonclustered Index Spool 操作アイコン](../../2014/database-engine/media/index-spool-32x.gif "Nonclustered Index Spool 操作アイコン")|**Index Spool**|**Index Spool**物理操作には、 `Argument`列に SEEK:() 述語が含まれています。 **Index Spool**操作は、入力行をスキャンし、隠しスプールファイル ( `tempdb`データベースに格納され、クエリの有効期間だけ存在する) に各行のコピーを配置し、行に非クラスター化インデックスを作成します。 さらに、インデックスのシーク機能を使用して、SEEK:() 述語に適合する行だけを出力します。 演算子が巻き戻し (たとえば、 `Nested Loops`演算子によって) されていても、再バインドが不要な場合は、入力を再スキャンする代わりにスプールされたデータが使用されます。|  
|![Nonclustered Index Update 操作アイコン](../../2014/database-engine/media/nonclust-index-update-32x.gif "Nonclustered Index Update 操作アイコン")|`Nonclustered Index Update`|物理`Nonclustered Index Update`操作は、 `Argument`列に指定された非クラスター化インデックスの入力から行を更新します。 SET:() 述語がある場合、更新される各列がこの値に設定されます。 `Nonclustered Index Update` は物理操作です。|  
|![Online Index Insert 操作アイコン](../../2014/database-engine/media/online-index-32x.gif "Online Index Insert 操作アイコン")|**Online Index Insert**|**Online Index Insert** 物理操作は、インデックスの作成操作、変更操作、または削除操作がオンラインで実行されることを示します。 つまり、インデックス操作の実行中に、基になるテーブル データをユーザーが利用することができます。|  
|None|`Parallelism`|操作`Parallelism`は、ストリームの分散、収集ストリーム、および再パーティション分割の論理操作を実行します。 列`Argument`には、パーティション分割される列のコンマ区切りリストを使用して、PARTITION columns:() 述語を含めることができます。 `Argument`列に ORDER BY:() 述語を含めることもできます。これは、パーティション分割中の並べ替え順序を保持するための列の一覧です。 `Parallelism` は物理操作です。<br /><br /> 注: クエリが並列クエリとしてコンパイルされている場合、実行時にはシリアルクエリとして実行されますが、SET STATISTICS XML またはの [ [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] **実際の実行プランを含める**] オプションを使用して`Parallelism`生成された Showplan 出力には、演算子の`RunTimeInformation`要素が含まれません。 SET STATISTICS PROFILE の出力では、実際の行数と実際の実行数によって、 `Parallelism`演算子の0が表示されます。 いずれかの条件が発生した場合`Parallelism` 、演算子は、実行時のクエリプランではなく、クエリのコンパイル中にのみ使用されたことを意味します。 サーバー上での同時実行の負荷が高い場合は、並列クエリ プランが直列に実行されることがあります。|  
|![Parameter Table Scan 操作アイコン](../../2014/database-engine/media/parameter-table-scan-32x.gif "Parameter Table Scan 操作アイコン")|`Parameter Table Scan`|`Parameter Table Scan` 操作により、現在のクエリのパラメーターとして機能しているテーブルをスキャンします。 通常、この操作は、ストアド プロシージャ内の INSERT クエリに対して使用されます。 `Parameter Table Scan` は論理操作でもあり、物理操作でもあります。|  
|None|**Partial Aggregate**|**Partial Aggregate** は、並列プランで使用されます。 ディスクへの書き込み ("スピル" と呼ばれます) が必要にならないように、できるだけ多くの入力行に集計関数が適用されます。 `Hash Match`は、パーティションの集計を実装する唯一の物理操作 (iterator) です。 **Partial Aggregate** は論理操作です。|  
|![Population Query カーソル操作アイコン](../../2014/database-engine/media/poulation-query-32x.gif "Population Query カーソル操作アイコン")|`Population Query`|`Population Query` 操作によって、カーソルが開かれたときにカーソルの作業テーブルを作成します。|  
|![Refresh Query カーソル操作アイコン](../../2014/database-engine/media/refresh-query-32x.gif "Refresh Query カーソル操作アイコン")|`Refresh Query`|`Refresh Query` 操作は、フェッチ バッファーから行の現在のデータをフェッチします。|  
|![Remote Delete 操作アイコン](../../2014/database-engine/media/remote-delete-32x.gif "Remote Delete 操作アイコン")|`Remote Delete`|`Remote Delete` 操作は、リモート オブジェクトから入力行を削除します。 `Remote Delete` は論理操作でもあり、物理操作でもあります。|  
|![Remote Index Seek プラン表示操作アイコン](../../2014/database-engine/media/remote-index-scan-32x.gif "Remote Index Seek プラン表示操作アイコン")|**Remote Index Scan**|**Remote Index Scan** 操作は、Argument 列に指定されたリモート インデックスをスキャンします。 **Remote Index Scan** は論理操作でもあり、物理操作でもあります。|  
|![Remote Index Seek プラン表示操作アイコン](../../2014/database-engine/media/remote-index-seek-32x.gif "Remote Index Seek プラン表示操作アイコン")|**Remote Index Seek**|**Remote Index Seek** 操作は、リモート インデックス オブジェクトのシーク機能を使用して行を取得します。 列`Argument`には、使用されているリモートインデックスの名前と SEEK:() 述語が含まれています。 **Remote Index Seek** は論理操作でもあり、物理操作でもあります。|  
|![Remote Insert 操作アイコン](../../2014/database-engine/media/remote-insert-32x.gif "Remote Insert 操作アイコン")|**Remote Insert**|**Remote Insert** 操作では、入力行がリモート オブジェクトに挿入されます。 **Remote Insert** は論理操作でもあり、物理操作でもあります。|  
|![Remote Query 操作アイコン](../../2014/database-engine/media/remote-query-32x.gif "Remote Query 操作アイコン")|`Remote Query`|`Remote Query` 操作では、リモート ソースにクエリを送信します。 リモートサーバーに送信されるクエリのテキストが`Argument`列に表示されます。 `Remote Query` は論理操作でもあり、物理操作でもあります。|  
|![Remote Scan 操作アイコン](../../2014/database-engine/media/remote-scan-32x.gif "Remote Scan 操作アイコン")|`Remote Scan`|`Remote Scan` 操作は、リモート オブジェクトをスキャンします。 リモートオブジェクトの名前が`Argument`列に表示されます。 `Remote Scan` は論理操作でもあり、物理操作でもあります。|  
|![Remote Update 操作アイコン](../../2014/database-engine/media/remote-update-32x.gif "Remote Update 操作アイコン")|`Remote Update`|`Remote Update` 操作は、リモート オブジェクトの入力行を更新します。 `Remote Update` は論理操作でもあり、物理操作でもあります。|  
|![Repartition Streams 並列処理操作アイコン](../../2014/database-engine/media/parallelism-repartition-stream.gif "Repartition Streams 並列処理操作アイコン")|**Repartition Streams**|**Repartition Streams** 操作では、複数のストリームを使用して、複数のレコードのストリームが生成されます。 レコードの内容と形式は変更されません。 クエリ オプティマイザーでビットマップ フィルターが使用される場合は、出力ストリームの行数が少なくなります。 入力ストリームの各レコードは、1 つの出力ストリームに配置されます。 この操作で順序を保持する場合、すべての入力ストリームが並べ替えられ、いくつかの並べ替え済みの出力ストリームにマージされる必要があります。 出力がパーティション分割されて`Argument`いる場合、列には PARTITION columns:() 述語とパーティション分割列が含まれます。出力が順序付けされて`Argument`いる場合、この列には ORDER BY:() 述語と順序付けされている列が含まれます。 **Repartition Streams** は論理操作です。 この操作は、並列クエリ プランのみで使用されます。|  
|![Result 言語要素アイコン](../../2014/database-engine/media/result-32x.gif "Result 言語要素アイコン")|`Result`|`Result` 操作は、クエリ プランの最後に返されるデータです。 これは通常、プラン表示のルート要素です。 `Result` は言語要素です。|  
|![RID Lookup 操作アイコン](../../2014/database-engine/media/rid-nonclust-locate-32x.gif "RID Lookup 操作アイコン")|`RID Lookup`|`RID Lookup` は、指定された行識別子 (RID) を使用する、ヒープ上のブックマーク参照です。 `Argument`列には、テーブル内の行を検索するために使用されるブックマークラベルと、行が検索されるテーブルの名前が含まれています。 `RID Lookup` は、常に NESTED LOOP JOIN を伴います。 `RID Lookup` は物理操作です。 ブックマーク参照の詳細については、MSDN の SQL Server ブログの「[ブックマーク参照](https://go.microsoft.com/fwlink/?LinkId=132568)」を参照してください。|  
|None|`Right Anti Semi Join`|`Right Anti Semi Join` 操作は、2 番目 (下部) の入力の中で最初 (上部) の入力に一致する行がない各行を出力します。 一致する行は、 `Argument`列の述語に適合する行として定義されます (述語が存在しない場合は、各行が一致する行になります)。 `Right Anti Semi Join` は論理操作です。|  
|None|`Right Outer Join`|`Right Outer Join` 操作は、2 番目 (下部) の入力と最初 (上部) の入力の一致行との結合に適合する各行を返します。 また、2 番目の入力に最初の入力に一致する行がない場合は、2 番目の入力が NULL と結合された行も返します。 `Argument`列に結合述語が存在しない場合は、各行が一致する行になります。 `Right Outer Join` は論理操作です。|  
|None|`Right Semi Join`|`Right Semi Join` 操作は、2 番目 (下部) の入力の中に最初 (上部) の入力と一致する行があれば、該当する行を返します。 `Argument`列に結合述語が存在しない場合は、各行が一致する行になります。 `Right Semi Join` は論理操作です。|  
|![Row Count Spool 操作アイコン](../../2014/database-engine/media/remote-count-spool-32x.gif "Row Count Spool 操作アイコン")|**Row Count Spool**|**Row Count Spool** 操作では入力がスキャンされて存在する行数がカウントされ、同数の行がデータなしで返されます。 この操作は、行に含まれているデータではなく、行の存在チェックが重要な場合に使用されます。 たとえば、演算子が`Nested Loops`左半結合演算を実行し、結合述語が内部入力に適用される場合、 `Nested Loops`演算子の内部入力の先頭に行カウントスプールが配置されることがあります。 次に`Nested Loops` 、行カウントスプールによって出力される行数 (内部側の実際のデータが不要であるため) を指定して、外側の行を返すかどうかを判断できます。 **Row Count Spool** は物理操作です。|  
|![Segment 操作アイコン](../../2014/database-engine/media/segment-32x.gif "Segment 操作アイコン")|**市場**|**Segment** は論理操作でもあり、物理操作でもあります。 この操作は、1 つまたは複数の列の値に基づいて入力セットをセグメントに分割します。 これらの列は、 **Segment** 操作に引数として表示されます。 この操作では、セグメントは 1 つずつ出力されます。|  
|None|`Segment Repartition`|並列クエリ プランでは、反復子に概念上の領域が存在する場合があります。 このような領域内にある反復子はすべて、並列スレッドにより実行できます。 領域自体は、順次実行される必要があります。 個別の領域内の `Parallelism` 反復子のいくつかは、`Branch Repartition` と呼ばれます。 このような 2 つの領域間の境界にある `Parallelism` 反復子は、`Segment Repartition` と呼ばれます。 `Branch Repartition` と `Segment Repartition` は論理操作です。|  
|![Sequence 操作アイコン](../../2014/database-engine/media/sequence-32x.gif "Sequence 操作アイコン")|`Sequence`|`Sequence` 操作によって、広範な更新プランを実行します。 機能的には、各入力を順次 (上から下へ) 実行します。 通常、各入力は異なるオブジェクトの更新です。 最後の (下部の) 入力からの行のみを返します。 `Sequence` は論理操作でもあり、物理操作でもあります。|  
|![Sequence Project 操作アイコン](../../2014/database-engine/media/sequence-project-32x.gif "Sequence Project 操作アイコン")|`Sequence Project`|`Sequence Project` 操作は、列を追加し、順序付けされたセットに対する計算を実行します。 この操作は、1 つまたは複数の列の値に基づいて入力セットをセグメントに分割します。 この操作では、セグメントは 1 つずつ出力されます。 これらの列は、`Sequence Project` 操作の引数として表示されます。 `Sequence Project` は論理操作でもあり、物理操作でもあります。|  
|![Snapshot カーソル操作アイコン](../../2014/database-engine/media/snapshot-32x.gif "Snapshot カーソル操作アイコン")|**スナップショット**|**Snapshot** 操作は、他のユーザーによる変更を表示しないカーソルを作成します。|  
|![Sort 操作アイコン](../../2014/database-engine/media/sort-32x.gif "Sort 操作アイコン")|`Sort`|操作`Sort`は、すべての受信行を並べ替えます。 この`Argument`列には、この操作によって重複が削除される場合は DISTINCT order by:() 述語が含まれています。また、並べ替えられる列のコンマ区切りリストを含む order by:() 述語が含まれています。 列を昇順に並べ替える場合は、列名の前に値 ASC が付きます。降順に並べ替える場合は、列名の前に値 DESC が付きます。 `Sort` は論理操作でもあり、物理操作でもあります。|  
|![Split 操作アイコン](../../2014/database-engine/media/split-32x.gif "Split 操作アイコン")|`Split`|操作`Split`は、更新処理を最適化するために使用されます。 この操作により、各更新操作が削除操作と挿入操作に分割されます。 `Split` は論理操作でもあり、物理操作でもあります。|  
|![Spool 操作アイコン](../../2014/database-engine/media/spool-32x.gif "Spool 操作アイコン")|**スプーラー**|**Spool**操作は、クエリの`tempdb`中間結果をデータベースに保存します。|  
|![Stream Aggregate 操作アイコン](../../2014/database-engine/media/stream-aggregate-32x.gif "Stream Aggregate 操作アイコン")|`Stream Aggregate`|`Stream Aggregate` 操作は、1 つ以上の列を基準にして行をグループ化し、クエリから返される 1 つ以上の集計式を計算します。 この操作の出力は、クエリ内のその後の操作から参照することも、クライアントに返すことも、あるいはその両方を行うこともできます。 `Stream Aggregate` 操作を使用するには、グループ内で列を基準にして入力を並べ替えておく必要があります。 並べ替えられたインデックスのシークやスキャンまたは前の `Sort` 操作が原因でデータがまだ並べ替えられていない場合は、オプティマイザーによって、この操作の前に `Sort` 操作が使用されます。 の[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]SHOWPLAN_ALL ステートメントまたはグラフィカルな実行プランでは、GROUP BY 述語の列が`Argument`列に一覧表示され、集計式が [**定義済みの値**] 列に一覧表示されます。 `Stream Aggregate` は物理操作です。|  
|![Switch 操作アイコン](../../2014/database-engine/media/switch-32x.gif "Switch 操作アイコン")|**切り替わり**|**Switch** は、 *n* 個の入力を取得する特殊な連結反復子です。 個々の **Switch** 操作には式が 1 つ関連付けられます。 *Switch*操作は式の戻り値 (0 から **n** -1 までの範囲) に応じて、適切な入力ストリームを出力ストリームにコピーします。 **Switch** 操作の用途の 1 つは、高速順方向専用カーソルを使用するクエリ プランに **TOP** などの特定の操作を実装することです。 **Switch** は論理操作でもあり、物理操作でもあります。|  
|![Table Delete 操作アイコン](../../2014/database-engine/media/table-delete-32x.gif "Table Delete 操作アイコン")|`Table Delete`|物理`Table Delete`操作は、クエリ実行プランの`Argument`列に指定されているテーブルから行を削除します。|  
|![Table Insert 操作アイコン](../../2014/database-engine/media/table-insert-32x.gif "Table Insert 操作アイコン")|`Table Insert`|操作`Table Insert`は、クエリ実行プランの`Argument`列に指定されたテーブルに、入力から行を挿入します。 また、`Argument` 列には、各列に設定する値を示す SET:() 述語も含まれます。 `Table Insert` に挿入値の子がない場合、挿入される行は、Insert 操作自体から取得されます。 `Table Insert` は物理操作です。|  
|![Table Merge 操作アイコン](../../2014/database-engine/media/table-merge-32x.gif "Table Merge 操作アイコン")|**Table Merge**|**Table Merge** 操作は、マージ データ ストリームをヒープに適用します。 操作は、演算子の`Argument`列で指定されたテーブルの行を削除、更新、または挿入します。 実際に実行される操作は、演算子の`Argument`列に指定された**アクション**列の実行時の値によって異なります。 **Table Merge** は物理操作です。|  
|![Table Scan 操作アイコン](../../2014/database-engine/media/table-scan-32x.gif "Table Scan 操作アイコン")|`Table Scan`|操作`Table Scan`は、クエリ実行プランの`Argument`列に指定されているテーブルからすべての行を取得します。 `Argument`列に WHERE:() 述語が含まれている場合、述語に適合する行だけが返されます。 `Table Scan` は論理操作でもあり、物理操作でもあります。|  
|![Table Spool 操作アイコン](../../2014/database-engine/media/table-spool-32x.gif "Table Spool 操作アイコン")|**Table Spool**|**Table Spool** 操作は入力をスキャンし、隠しスプール テーブルに各行のコピーを格納します。この隠しスプール テーブルは [tempdb](../relational-databases/databases/tempdb-database.md) データベースに格納され、クエリの有効期間だけ存在します。 演算子が巻き戻し (たとえば、 `Nested Loops`演算子によって) されていても、再バインドが不要な場合は、入力を再スキャンする代わりにスプールされたデータが使用されます。 **Table Spool** は物理操作です。|  
|![Table Update 操作アイコン](../../2014/database-engine/media/table-update-32x.gif "Table Update 操作アイコン")|`Table Update`|物理`Table Update`操作は、クエリ実行プランの`Argument`列に指定されているテーブルの入力行を更新します。 SET:() 述語によって、更新された各列の値が決定されます。 これらの値は、SET 句、またはこの操作内かこのクエリ内で参照されることがあります。|  
|![Table-valued Function 操作アイコン](../../2014/database-engine/media/table-valued-function-32x.gif "Table-valued Function 操作アイコン")|**テーブル値関数**|**Table-valued Function** 操作は、テーブル値関数 ( [!INCLUDE[tsql](../includes/tsql-md.md)] または CLR のいずれか) を評価し、結果行を [tempdb](../relational-databases/databases/tempdb-database.md) データベースに格納します。 親の反復子が行を要求すると、**テーブル値関数**はから`tempdb`行を返します。<br /><br /> テーブル値関数への呼び出しを伴うクエリにより、 **Table-valued Function** 反復子を備えたクエリ プランが生成されます。 さまざまなパラメーター値を使用して**Table-valued Function** を評価できます。<br /><br /> **Table-valued Function XML Reader** では、パラメーターとして XML BLOB が入力され、XML ノードを表す行セットが XML ドキュメントの順序で生成されます。 他の入力パラメーターにより、XML ドキュメントのサブセットに返される XML ノードが制限されることがあります。<br /><br /> **Table Valued Function XML Reader with XPath filter** は、出力を XPath 式が満たされる XML ノードに限定する、特殊な種類の **XML Reader Table-valued Function** です。<br /><br /> <br /><br /> **Table-valued Function** は論理操作でもあり、物理操作でもあります。|  
|![Top 操作アイコン](../../2014/database-engine/media/top-32x.gif "Top 操作アイコン")|**ページのトップへ**|**Top** 操作は、入力をスキャンし、並べ替え順に基づいて、指定した最初の数または最初の比率の行だけを返します。 列`Argument`には、結合のチェック対象となる列の一覧を含めることができます。 **Top** 操作は、更新プランで行数制限を行うときに使用します。 **Top** は論理操作でもあり、物理操作でもあります。 **Top** は論理操作でもあり、物理操作でもあります。|  
|None|**Top N Sort**|**Top n Sort**は`Sort`反復子に似ていますが、結果セット全体ではなく、最初の*n*行だけが必要です。 *N*の値が小さい場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクエリ実行エンジンは、メモリ内全体の並べ替え操作を実行しようとします。 *N*の値が大きい場合、クエリ実行エンジンは、 *N* をパラメーターとしない、より汎用的な並べ替え方法を使用します。|  
|![拡張操作 (UDX) のアイコン](../../2014/database-engine/media/udx-32x.gif "拡張操作 (UDX) のアイコン")|`UDX`|拡張操作 (UDX) には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の数ある操作のうちの XQuery 操作と XPath 操作が実装されています。 すべての UDX 操作には、論理操作と物理操作の両方があります。<br /><br /> 拡張操作 (UDX) `FOR XML` は、単一出力行の単一 BLOB 列に XML 表記で入力するリレーショナル行セットをシリアル化するのに使用します。 この操作は、順序を区別する XML 集計操作です。<br /><br /> 拡張操作 (UDX) `XML SERIALIZER` は、順序を区別する XML 集計操作です。 この操作は、XML ドキュメントの順序で XML ノードまたは XQuery スカラーを表す行を入力し、単一出力行の単一 XML 列にシリアル化した XML BLOB を生成します。<br /><br /> 拡張操作 (UDX) `XML FRAGMENT SERIALIZER` は、XQuery の挿入データの変更拡張に挿入される XML フラグメントを表す入力行の処理に使用する `XML SERIALIZER` の特殊な形式の操作です。<br /><br /> 拡張操作 (UDX) `XQUERY STRING` は、XML ノードを表す入力行の XQuery 文字列値を評価します。 これは順序を区別する文字列集計操作です。 この操作では、入力の文字列値を含む XQuery スカラーを表す列を持つ 1 行が出力されます。<br /><br /> 拡張操作 (UDX) `XQUERY LIST DECOMPOSER` は、XQuery のリスト分解操作です。 入力が XSD リストで想定されている型の場合、この操作では、XML ノードを表す入力行ごとに、リスト要素の値を含む XQuery スカラーを表す 1 行以上の行が生成されます。<br /><br /> 拡張操作 (UDX) `XQUERY DATA` は、XML ノードを表す入力の XQuery の fn:data() 関数を評価します。 これは順序を区別する文字列集計操作です。 この操作では、 **fn:data()** 関数の結果を含む XQuery スカラーを表す列を持つ 1 行が出力されます。<br /><br /> 拡張操作 `XQUERY CONTAINS` は、XML ノードを表す入力の XQuery の fn:contains() 関数を評価します。 これは順序を区別する文字列集計操作です。 この操作では、 **fn:contains()** 関数の結果を含む XQuery スカラーを表す列を持つ 1 行が出力されます。<br /><br /> 拡張操作`UPDATE XML NODE`は、xml 型の**modify ()** メソッドで XQuery 置換データ変更拡張の xml ノードを更新します。|  
|None|**組合**|**Union** 操作は、複数の入力をスキャンし、重複行を削除して、スキャンした各行を出力します。 **Union** は論理操作です。|  
|![Update (データベース エンジン) 操作アイコン](../../2014/database-engine/media/update-32x.gif "Update (データベース エンジン) 操作アイコン")|`Update`|操作`Update`は、クエリ実行プランの`Argument`列に指定されているオブジェクトの入力から各行を更新します。 `Update` は論理操作です。 物理操作には、`Table Update`、`Index Update`、および `Clustered Index Update` があります。|  
|![While 言語要素アイコン](../../2014/database-engine/media/while-32x.gif "While 言語要素アイコン")|`While`|`While` 操作は [!INCLUDE[tsql](../includes/tsql-md.md)] while ループを実装します。 `While`は言語要素です|  
|![Table Spool 操作アイコン](../../2014/database-engine/media/table-spool-32x.gif "Table Spool 操作アイコン")|`Window Spool`|`Window Spool` 操作は、各行をその行に関連付けられたウィンドウを表す行セットに拡張します。 クエリでは、OVER 句でクエリの結果セット内のウィンドウを定義してから、ウィンドウ関数がウィンドウ内の各行の値を計算します。 `Window Spool` は論理操作でもあり、物理操作でもあります。|  
  
  
