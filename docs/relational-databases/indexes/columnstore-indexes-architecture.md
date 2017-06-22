---
title: "列ストア インデックス - アーキテクチャ | Microsoft Docs"
ms.custom: 
ms.date: 01/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96b8e884-8244-425f-b856-72a8ff6895a6
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 835e3acd76972eef01b4d286cbc1f6ecf6fac605
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="columnstore-indexes---architecture"></a>列ストア インデックス - アーキテクチャ
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

列ストア インデックスを構築する方法について説明します。 これらの基本を理解すると、効果的に使用する方法を説明する、その他の列ストアの記事を理解しやすくなります。

## <a name="data-storage-uses-columnstore-and-rowstore-compression"></a>データ ストレージでは列ストアと行ストアの圧縮を使用する
列ストア インデックスの説明では、データ ストレージの形式を強調する目的で *行ストア* と *列ストア* という用語を使用しています。  列ストア インデックスでは、両方の種類のストレージを使用します。

 ![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")

- **列ストア** は、行と列を含むテーブルとして論理的に編成され、列方向のデータ形式で物理的に格納されているデータです。
  
列ストア インデックスでは、ほとんどのデータを列ストア形式で物理的に格納します。 列ストア形式では、データは列として圧縮および非圧縮されます。 クエリで要求されない行ごとに、その他の値を非圧縮する必要はありません。 このため、大規模なテーブルの列全体を高速にスキャンできます。 

- **行ストア** は、行と列を含むテーブルとして論理的に編成され、行方向のデータ形式で物理的に格納されているデータです。 これは、ヒープまたはクラスター化された "btree" インデックスなどのリレーショナル テーブル データを格納する従来の方法です。

また、列ストア インデックスでは、デルタストアという行ストア形式で一部の行を物理的にも格納します。 デルタストア (デルタ行グループとも呼ばれます) は、列ストアへの圧縮に適合させるために、数が少なすぎる行を格納する場所です。 デルタ行グループはそれぞれ、クラスター化された btree インデックスとして実装されます。 

- **デルタストア**は、列ストアに圧縮するには数が少なすぎる行を保持する場所です。 デルタストアは行ストアです。 
  
## <a name="operations-are-performed-on-rowgroups-and-column-segments"></a>操作は行グループと列セグメント上で実行される

列ストア インデックスでは、行を管理可能な単位にグループ化します。 これらの単位はそれぞれ、行グループと呼ばれます。 最適なパフォーマンスを得るため、行グループ内の行数は、高い圧縮率が実現される程度に多く、インメモリ操作の利点を得られる程度に少ないです。

* **行グループ**は、列ストア インデックスが管理および圧縮の操作を実行する行のグループです。 

たとえば、列ストア インデックスは、行グループで次の操作を実行します。

* 行グループを列ストアに圧縮します。 圧縮は、行グループ内の各列セグメントで実行されます。
* ALTER INDEX REORGANIZE 操作中に行グループをマージします。
* ALTER INDEX REBUILD 操作中に新しい行グループを作成します。
* 動的管理ビュー (DMV) の行グループの正常性と断片化に関するレポートを行います。

デルタストアは、デルタ行グループと呼ばれる 1 つ以上の行グループで構成されます。 各デルタ行グループは、列ストアに圧縮するには少なすぎる場合に、行を格納するクラスター化された btree インデックスです。  

* **デルタ行グループ**は、1,048,576 個の行が含まれるまで、またはインデックスが再構築されるまで、小規模の一括読み込みと挿入を格納するクラスター化された btree インデックスです。  デルタ行グループに 1,048, 576 個の行が含まれると、閉じられたと見なされ、列ストアに圧縮するための組ムーバーと呼ばれるプロセスを待ちます。 


それぞれの列には、行グループごとにその値の一部が含まれます。 これらの値は列セグメントと呼ばれます。 列ストア インデックスが行グループを圧縮する場合、各列セグメントを個別に圧縮します。 列全体を非圧縮する場合、列ストア インデックスでは、それぞれの行グループから列セグメントを 1 つ非圧縮するだけで列全体を非圧縮できます。

* **列セグメント**は、行グループ内の列の値の一部です。 それぞれの行グループには、テーブルの 1 つの列につき 1 つの列セグメントが含まれます。 それぞれの列には、行グループごとに 1 つの列セグメントがあります。| 
  
 ![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
 
## <a name="small-loads-and-inserts-go-to-the-deltastore"></a>小規模の読み込みと挿入はデルタストアに移動される
列ストア インデックスは、一度に少なくとも 102,400 個の行を列ストア インデックスに圧縮することで、列ストア インデックスの圧縮とパフォーマンスを向上させています。 行を一括で圧縮するために、列ストア インデックスでは、小規模な読み込みを累積し、デルタストアに挿入します。 デルタストア操作は内部で処理されます。 列ストア インデックスは、正しいクエリ結果を返すために、列ストアとデルタストアの両方からのクエリ結果を結合します。 

次の場合に、行はデルタストアに移動されます。
* INSERT INTO VALUES ステートメントで挿入された場合。
* 一括読み込みの最後で 102,400 未満の場合。
* 更新済み。 更新はそれぞれ、削除および挿入として実装されます。

また、デルタストアでは、削除済みとしてマークされているが、列ストアから物理的に削除されていない、削除された行の ID の一覧も格納します。 

## <a name="when-delta-rowgroups-are-full-they-get-compressed-into-the-columnstore"></a>デルタ行グループが満たされた場合、列ストアに圧縮される

クラスター化列ストア インデックスでは、デルタ行グループごとに最大 1,048,576 個の列を収集してから、行グループを列ストアに圧縮します。 これにより、列ストア インデックスの圧縮が向上します。 デルタ行グループに 1,048,576 個の行が含まれている場合、列ストア インデックスは列グループが閉じられたと見なします。 *組ムーバー*というバックグラウンド プロセスでは、閉じられた行グループを見つけて、それを列ストアに圧縮します。 

インデックスを再構築または再構成するには、[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) を使用してデルタ行グループを列ストアに強制的に圧縮することができます。  圧縮中にメモリ負荷がある場合、列ストア インデックスは圧縮行グループ内の行数を減らす可能性があることに注意してください。

## <a name="each-table-partition-has-its-own-rowgroups-and-delta-rowgroups"></a>各テーブル パーティションには、独自の行グループとデルタ行グループが含まれる

パーティション分割の概念は、クラスター化インデックス、ヒープ、および列ストア インデックスのすべてにおいて同じです。 テーブルのパーティション分割では、列の値の範囲に従って、テーブルをより小規模の列のグループに分割します。 通常、これはデータを管理するために使用されます。 たとえば、データの年ごとにパーティションを作成して、パーティションの切り替えを使用し、データをコストが低いストレージにアーカイブすることができます。 パーティションの切り替えは、列ストア インデックス上で動作するため、データのパーティションを別の場所に移動しやすくなります。

行グループは常に、テーブル パーティション内に定義されます。 列ストア インデックスがパーティション分割されると、各パーティションには独自の圧縮行グループとデルタ行グループが含まれます。

### <a name="each-partition-can-have-multiple-delta-rowgroups"></a>各パーティションに複数のデルタ行グループを含めることができる
各パーティションに複数のデルタ行グループを含めることができます。 列ストア インデックスでデータをデルタ行グループに追加する必要があり、デルタ行グループがロックされている場合、列ストア インデックスでは、さまざまなデルタ行グループのロックを取得しようとします。 使用できるデルタ行グループがない場合は、列ストア インデックスでは新しいデルタ行グループが作成されます。  たとえば、パーティションが 10 個のテーブルには、簡単に 20 個以上のデルタ行グループを含めることができます。 

  
## <a name="you-can-combine-columnstore-and-rowstore-indexes-on-the-same-table"></a>同じテーブルで列ストア インデックスと行ストア インデックスを結合できる
非クラスター化インデックスには、基になるテーブルの行と列の一部または全体のコピーが含まれています。 インデックスはテーブルの 1 つ以上の列として定義され、行のフィルター処理条件をオプションで設定できます。 

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、更新可能な非クラスター化列ストア インデックスを、行ストア テーブルに作成できます。 列ストア インデックスは、データのコピーを格納するため、追加のストレージが必要です。 ただし、列ストア インデックス内のデータは、行ストア テーブルが必要とするサイズよりも小さいサイズに圧縮されます。  これにより、同時に、列ストア インデックスの分析と行ストア インデックスのトランザクションを同時に実行できます。 行ストア テーブルでデータが変更されると列ストアが更新されます。したがって、両方のインデックスが、同じデータに対して作業を行うことになります。  
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、列ストア インデックスでは、1 つ以上の非クラスター化行ストア インデックスを使用できます。 これにより、基になる列ストアで、効率的なテーブル シークを実行できます。 他のオプションも使用できます。 たとえば、行ストア テーブルで UNIQUE 制約を使用することで、主キー制約を適用できます。 一意でない値は行ストア テーブルに挿入できないため、SQL Server でその値を列ストアに挿入することはできません。  
 

## <a name="metadata"></a>メタデータ  
これらのメタデータ ビューを使って、列ストア インデックスの属性を表示します。 多くのアーキテクチャ情報が、これらのビューの一部に埋め込まれます。

列ストア インデックス内のすべての列は、付加列としてメタデータに格納されることに注意してください。 列ストア インデックスにキー列はありません。  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
-   [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
-   [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
  
-   [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)  
  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)  
  
-   [sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)  
  
-   [sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
|  


## <a name="next-steps"></a>次の手順
 列ストア インデックスをデザインするガイダンスについては、「[列ストア インデックス - デザイン ガイダンス](../../relational-databases/indexes/columnstore-indexes-design-guidance.md)」を参照してください。

