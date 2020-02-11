---
title: クラスター化列ストアインデックスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e65c3e277eb9a3e5e3703525b9c1ac06b423c96
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62773741"
---
# <a name="using-clustered-columnstore-indexes"></a>クラスター化列ストア インデックスの使用
  
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクラスター化 columnstore インデックスを使用するタスクです。  
  
 列ストアインデックスの概要については、「[列ストアインデックス](../relational-databases/indexes/columnstore-indexes-described.md)の概要」を参照してください。  
  
 クラスター化列ストアインデックスの詳細については、「[クラスター化列ストアインデックスの使用](../relational-databases/indexes/indexes.md)」を参照してください。  
  
## <a name="contents"></a>内容  
  
-   [クラスター化列ストア インデックスを作成する](#create)  
  
-   [クラスター化 Columnstore インデックスの削除](#drop)  
  
-   [クラスター化 Columnstore インデックスへのデータの読み込み](#load)  
  
-   [クラスター化 Columnstore インデックス内のデータの変更](#change)  
  
-   [クラスター化列ストアインデックスを再構築する](#rebuild)  
  
-   [クラスター化列ストアインデックスの再編成](#reorganize)  
  
##  <a name="create"></a>クラスター化列ストアインデックスを作成する  
 クラスター化列ストアインデックスを作成するには、まずヒープまたはクラスター化インデックスとして行ストアテーブルを作成し、次に[CREATE CLUSTERED 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)ステートメントを使用して、テーブルをクラスター化列ストアインデックスに変換します。 クラスター化 columnstore インデックスにクラスター化インデックスと同じ名前を付ける場合は、DROP_EXISTING オプションを使用します。  
  
 この例では、テーブルをヒープとして作成してから、cci_Simple という名前のクラスター化 columnstore インデックスに変換します。 こうすることで、テーブル全体のストレージが行ストアから列ストアに変更されます。  
  
```  
CREATE TABLE T1(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;  
GO  
```  
  
 詳細については、「 [CREATE CLUSTERED INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)」の「例」を参照してください。  
  
##  <a name="drop"></a>クラスター化列ストアインデックスを削除する  
 [DROP INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/drop-index-transact-sql)ステートメントを使用して、クラスター化列ストアインデックスを削除します。 この操作は、インデックスを削除し、列ストア テーブルを行ストア ヒープに変換します。  
  
##  <a name="load"></a>クラスター化列ストアインデックスへのデータの読み込み  
 標準的な読み込み方法を使用して既存のクラスター化列ストア インデックスにデータを追加できます。  たとえば、bcp 一括読み込みツール、Integration Services、挿入...[すべてのデータをクラスター化列ストアインデックスに読み込むことができる] を選択します。  
  
 クラスター化 columnstore インデックスでは、columnstore の列セグメントの断片化を防ぐためにデルタストアを活用します。  
  
### <a name="loading-into-a-partitioned-table"></a>パーティションテーブルへの読み込み  
 パーティション分割されたデータの場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はまずパーティションに各行を割り当て、次にパーティション内のデータの columnstore 処理を実行します。 各パーティションには、独自の行グループと少なくとも 1 つのデルタストアがあります。  
  
### <a name="deltastore-loading-scenarios"></a>デルタストアの読み込みのシナリオ  
 デルタストアの行は、行グループに許容されている最大行数になるまで蓄積されます。 デルタストアに行グループあたりの最大行数が含まれている[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]場合は、行グループを "CLOSED" としてマークします。 "組ムーバー" と呼ばれるバックグラウンドプロセスは、閉じられた行グループを検索し、列ストアに移動します。ここでは、行グループが列セグメントに圧縮され、列セグメントが列ストアに格納されます。  
  
 各クラスター化 columnstore インデックスに対して複数のデルタストアが許容されます。  
  
-   デルタストアがロックされている場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は別のデルタストアのロックを獲得しようとします。 使用できるデルタストアがない場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は新しいデルタストアを作成します。  
  
-   パーティション テーブルでは、各パーティションに 1 つ以上のデルタストアが許容されます。  
  
 クラスター化 columnstore インデックスのみについて、次のシナリオは、読み込まれた行が columnstore に直接移動するときと、デルタストアに移動するときについて説明します。  
  
 この例では、行グループはそれぞれ 102,400 ～ 1,048,576 個の行を持つことができます。  
  
|一括読み込みを行う行|列ストアに追加される行|デルタストアに追加される行|  
|-----------------------|-----------------------------------|----------------------------------|  
|102,000|0|102,000|  
|145,000|145,000<br /><br /> 行グループのサイズ: 145,000|0|  
|1,048,577|1,048,576<br /><br /> 行グループのサイズ: 1,048,576|1 で保護されたプロセスとして起動されました|  
|2,252,152|2,252,152<br /><br /> 行グループのサイズ: 1,048,576、1,048,576、155,000|0|  
  
 次の例は、1,048,577 個の行をパーティションに読み込んだ結果を示しています。 この結果では、列ストアに 1 つの圧縮された行グループ (圧縮された列セグメントとして)、およびデルタストアに 1 行があります。  
  
```  
SELECT * FROM sys.column_store_row_groups  
```  
  
 ![バッチ読み込みの rowgroup と deltastore](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "バッチ読み込みの rowgroup と deltastore")  
  

  
##  <a name="change"></a>クラスター化列ストアインデックスのデータの変更  
 クラスター化 columnstore インデックスでは挿入、更新、および DML 削除操作がサポートされます。  
  
 [Insert &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)を使用して行を挿入します。 行はデルタストアに追加されます。  
  
 
  [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) を使用して行を削除します。  
  
-   行が列ストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークしますが、インデックスが再構築されるまで行の物理ストレージを再確保することはありません。  
  
-   行がデルタストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は論理的および物理的に行を削除します。  
  
 
  [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) を使用して行を更新します。  
  
-   行が列ストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークし、更新された行をデルタストアに挿入します。  
  
-   行がデルタストアにある場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、デルタストアの行を更新します。  
  
##  <a name="rebuild"></a>クラスター化列ストアインデックスを再構築する  
 [CREATE CLUSTERED 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)または[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を使用して、既存のクラスター化列ストアインデックスの完全な再構築を実行します。 また、ALTER INDEX...再構築して特定のパーティションを再構築します。  
  
### <a name="rebuild-process"></a>再構築プロセス  
 クラスター化列ストア インデックスを再構築する際、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は以下のように動作します。  
  
-   再構築が行われている間、テーブルまたはパーティションを排他的にロックします。  再構築の間、データは "オフライン" になって使用できません。  
  
-   テーブルから論理的に削除された行を物理的に削除することで、列ストアをデフラグします。削除されたバイトは物理メディアで再利用されます。  
  
-   インデックスを再構築する前に、デルタストアの行ストア データを columnstore のデータとマージします。 再構築が終了すると、すべてのデータが columnstore 形式で格納され、デルタストアが空になります。  
  
-   すべてのデータを列ストアに再圧縮します。 再構築が行われている間、列ストア インデックスのコピーが 2 つ存在します。 再構築が完了したら、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] により、元の列ストア インデックスが削除されます。  
  
### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a>クラスター化 Columnstore インデックスの再構築の推奨設定  
 クラスター化 columnstore インデックスを再構築すると、断片化の解消およびすべての行を columnstore に移動する場合に便利です。 次の推奨事項が用意されています。  
  
-   テーブル全体ではなくパーティションを再構築します。  
  
    1.  インデックスが大きいとテーブル全体の再構築には時間がかかり、再構築中にインデックスの追加コピーを格納するために十分なディスク領域が必要です。 通常は、最近使用されたパーティションを再構築するだけで済みます。  
  
    2.  パーティション テーブルでは、columnstore インデックス全体を再構築する必要はありません。断片化は最近変更されたパーティションのみで起きる可能性が高いためです。 ファクト テーブルや大きなディメンション テーブルは通常、テーブルのチャンク上でバックアップおよび管理を行うためにパーティション分割されます。  
  
-   負荷の高い DML 操作後にパーティションを再構築します。  
  
     パーティションを再構築すると、パーティションの断片化を解消し、ディスク ストレージが減少します。 再構築すると、削除のマークが付けられた columnstore からすべての行が削除され、すべての行がデルタストアから columnstore に移動されます。  
  
-   データを読み込んだ後に、パーティションを再構築します。  
  
     これにより、すべてデータが columnstore に格納されます。 複数の負荷が同時に発生した場合は、各パーティションは複数のデルタストアを持つ可能性があります。 再構築すると、すべてのデルタストア行が columnstore に移動されます。  
  
##  <a name="reorganize"></a>クラスター化列ストアインデックスの再編成  
 クラスター化 columnstore インデックスを再構成すると、すべての CLOSED 行グループが columnstore に移動されます。 再編成を実行するには、 [ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)を再構成オプションと共に使用します。  
  
 再構成は、CLOSED 行グループを columnstore に移動するためには必要はありません。 組ムーバープロセスは、最終的にすべての閉じた行グループを検索して移動します。 ただし、組ムーバーはシングルスレッドであり、ワークロードに対して十分な速度で行グループを移動することはできません。  
  
### <a name="recommendations-for-reorganizing"></a>再構成に関する推奨事項  
 クラスター化列ストア インデックスを再構成するとき:  
  
-   クエリのパフォーマンスの利点をできるだけ早く得るために、1 つ以上のデータが読み込まれた後にクラスター化列ストア インデックスを再編成します。 再構成ではデータを圧縮するために最初に追加の CPU リソースが必要とされ、システムの全体的なパフォーマンスが遅くなる場合があります。 しかし、データが圧縮されるとすぐにクエリ パフォーマンスが改善します。  
  
  
