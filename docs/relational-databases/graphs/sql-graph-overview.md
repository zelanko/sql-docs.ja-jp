---
title: SQL Server と Azure SQL Database でのグラフ処理 |Microsoft Docs
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
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 276ef0d34d04f58b0b23b213dc52faf5b404693e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43101812"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>SQL Server と Azure SQL Database でのグラフ処理
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 多対多リレーションシップをモデル化するグラフ データベース機能を提供します。 グラフのリレーションシップが統合[!INCLUDE[tsql-md](../../includes/tsql-md.md)]受信を使用する利点と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]基礎となるデータベース管理システムとして。


## <a name="what-is-a-graph-database"></a>グラフ データベースとは何ですか。  
グラフ データベースはノード (または頂点) のコレクションと端 (または関係)。 (たとえば、個人または組織) エンティティを表すノードとエッジ (いいねや友人など) に接続されている 2 つのノード間のリレーションシップを表します。 ノードとエッジの両方には、それらに関連付けられたプロパティがある場合があります。 グラフ データベースを一意にいくつかの機能を次に示します。  
-   エッジまたはリレーションシップは、グラフ データベースでのファースト クラスのエンティティでありできます属性またはプロパティに関連付けられています。 
-   1 つのエッジは、グラフ データベース内の複数のノードを柔軟に接続できます。
-   パターン マッチングとマルチホップ ナビゲーション クエリを簡単に表現できます。
-   推移的閉包およびポリモーフィックなクエリを簡単に表現できます。

## <a name="when-to-use-a-graph-database"></a>グラフ データベースを使用する場合

何もないグラフ データベースを実現できる、リレーショナル データベースを使用して実現することはできません。 ただし、グラフ データベースやすく特定の種類のクエリを表現します。 また、特定の最適化を有効に特定のクエリ パフォーマンスが向上します。 次の要因に基づいて、他のいずれかを選択する決定できます。  
-   アプリケーションでは、階層データを持ちます。 HierarchyID データ型は、階層を実装するために使用できますが、いくつかの制限があります。 たとえば、複数の親ノードを格納することもできません。
-   アプリケーションが複雑な多対多リレーションシップです。アプリケーションの進化に伴って、新しいリレーションシップが追加されます。
-   相互接続されたデータとのリレーションシップを分析する必要があります。

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>導入されたグラフ機能 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
SQL Server の格納とクエリのグラフ データを簡単にグラフの拡張機能を追加が開始します。 最初のリリースでは、次の機能が導入されました。 


### <a name="create-graph-objects"></a>グラフのオブジェクトを作成します。
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] 拡張機能により、ノードまたはエッジ テーブルを作成するユーザー。 ノードとエッジの両方が、それらに関連付けられているプロパティを持つことができます。 以降、ノードとエッジ テーブルとして格納されます、リレーショナル テーブルでサポートされているすべての操作ノードまたはエッジ テーブルでサポートされます。 次に例を示します。  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![テーブル-人の友人](../../relational-databases/graphs/media/person-friends-tables.png "/people/person ノードや友人のエッジ テーブル")  
ノードとエッジ テーブルとして格納されます。  

### <a name="query-language-extensions"></a>クエリ言語の拡張機能  
新しい`MATCH`パターン マッチングと graph を通じて、マルチホップ ナビゲーションをサポートするために句が導入されました。 `MATCH`関数はパターン マッチングの ASCII アート形式の構文を使用します。 以下に例を示します。  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>完全に統合された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジン 
グラフの拡張機能は統合されます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジン。 同じストレージ エンジン、メタデータ、クエリ プロセッサなどを使用して格納し、グラフ データを照会します。 これにより、グラフおよびリレーショナル データを 1 つのクエリにわたりクエリを実行できます。 ユーザーは他のグラフ機能を組み合わせることからも利用できるよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列ストア、HA、R services でのようなテクノロジなど。SQL グラフ データベースは、すべてのセキュリティとコンプライアンスで使用できる機能もサポートしています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。
 
### <a name="tooling-and-ecosystem"></a>ツールとエコシステム  
ユーザーは、既存のツールおよびエコシステムによってメリットを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を提供します。 バックアップと復元などのツールのインポートし、エクスポート、すぐ BCP だけ作業します。 その他のツールまたは SSIS、SSRS、PowerBI などのサービスは、グラフ テーブルでは、リレーショナル テーブルで動作する方法です。
 
 ## <a name="next-steps"></a>次の手順  
読み取り、 [SQL グラフ データベース - アーキテクチャ](./sql-graph-architecture.md)
   

