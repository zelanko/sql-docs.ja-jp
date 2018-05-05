---
title: SQL Server と Azure SQL Database を使用した処理グラフ |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: graphs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 8c2ad7f5b31a97de5d0bfb22074b55bd61bb825b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>SQL Server と Azure SQL Database を使用した処理グラフ
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 多対多リレーションシップをモデル化するグラフのデータベース機能を提供します。 グラフのリレーションシップに統合されて[!INCLUDE[tsql-md](../../includes/tsql-md.md)]を使用する利点を享受し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]基本的なデータベース管理システムとして。


## <a name="what-is-a-graph-database"></a>グラフのデータベースとは何ですか。  
グラフのデータベースは、ノード (または頂点) の集まりとエッジ (リレーションシップ)。 (たとえば、個人または組織) のエンティティを表すノードとエッジが接続する (なや友人など) の 2 つのノード間のリレーションシップを表します。 両方のノードとエッジには、それらに関連付けられたプロパティがある場合があります。 グラフのデータベースを一意にいくつかの機能を次に示します。  
-   エッジまたはリレーションシップはグラフ データベース内の最初のクラスのエンティティでありできます属性またはプロパティに関連付けられています。 
-   単一のエッジは、グラフのデータベース内の複数のノードを柔軟に接続できます。
-   パターン マッチとマルチホップ ナビゲーション クエリを簡単に表現することができます。
-   推移的閉包およびポリモーフィック クエリを簡単に表現することができます。

## <a name="when-to-use-a-graph-database"></a>グラフのデータベースを使用する場合

ありませんグラフ データベースを達成できる、することは、リレーショナル データベースを使用します。 ただし、graph データベース易くなりますを特定の種類のクエリを表現します。 また、特定の最適化を有効に特定のクエリ パフォーマンスが向上します。 次の要因に基づいての決定、他の中の 1 つを選択することができます。  
-   アプリケーションでは、階層データを持ちます。 HierarchyID データ型は、階層を実装に使用できますが、いくつかの制限があります。 たとえば、ノードの複数の親を格納することもできません。
-   アプリケーションが複雑な多対多のリレーションシップです。アプリケーションの進化に伴って新しいリレーションシップが追加されます。
-   相互接続されたデータとのリレーションシップを分析する必要があります。

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>導入されたグラフ機能 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
SQL server、グラフ データの格納とクエリの実行が容易にグラフの拡張機能を追加する開始します。 最初のリリースでは、次の機能が導入されました。 


### <a name="create-graph-objects"></a>グラフのオブジェクトを作成します。
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] 拡張機能はノードまたはエッジ テーブルを作成するようにします。 両方のノードとエッジは、それに関連付けられたプロパティを持つことができます。 以降、ノードとエッジがテーブルとして格納されている、リレーショナル テーブルでサポートされているすべての操作ノードまたはエッジ テーブルでサポートされます。 次に例を示します。  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![ユーザーの友人-テーブル](../../relational-databases/graphs/media/person-friends-tables.png "//people/person ノードや友人のエッジ テーブル")  
ノードとエッジがテーブルとして格納されています。  

### <a name="query-language-extensions"></a>クエリ言語の拡張機能  
新しい`MATCH`パターン マッチと graph を通じてマルチホップ ナビゲーションをサポートするために句が導入されました。 `MATCH`関数はパターン一致の ASCII アート形式の構文を使用します。 以下に例を示します。  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>完全に統合された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジン 
グラフの拡張機能は完全に統合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジンです。 同じストレージ エンジン、メタデータ、クエリ プロセッサなどを保存し、グラフ データを照会する使用します。 これにより、ユーザーは、グラフと 1 つのクエリでリレーショナル データをまたいでクエリを実行できます。 ユーザーは他のグラフ機能を組み合わせることからも利用できるよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テクノロジなどの列ストア、HA、R services, などです。データベース ファイルのグラフは、すべてのセキュリティとコンプライアンス機能で使用可能なもサポートしています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
 
### <a name="tooling-and-ecosystem"></a>ツールとエコシステム  
ユーザーが既存のツールとエコシステムを利用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を提供します。 バックアップと復元などのツールのインポートし、エクスポート、すぐ BCP だけ作業します。 その他のツールまたは SSIS、SSRS PowerBI などのサービスでは動作グラフ テーブル リレーショナル テーブルで処理する方法だけです。
 
 ## <a name="next-steps"></a>次の手順  
読み取り、 [SQL グラフ データベース - アーキテクチャ](./sql-graph-architecture.md)
   

