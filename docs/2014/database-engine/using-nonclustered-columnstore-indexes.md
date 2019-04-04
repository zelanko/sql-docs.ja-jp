---
title: 非クラスター化列ストア インデックスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e97aed3a5a4f5b49e482479b58928d2092a314f9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182501"
---
# <a name="using-nonclustered-columnstore-indexes"></a>非クラスター化列ストア インデックスの使用
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルの非クラスター化 columnstore インデックスを使用するキー タスクについて説明します。  
  
 列ストア インデックスの概要については、[列ストア インデックスの概念](../relational-databases/indexes/columnstore-indexes-described.md)を参照してください。  
  
 クラスター化列ストア インデックスについては、[クラスター化列ストア インデックスを使用して](../relational-databases/indexes/indexes.md)を参照してください。  
  
## <a name="contents"></a>目次  
  
-   [非クラスター化列ストア インデックスを作成します。](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [非クラスター化列ストア インデックス内のデータを変更します。](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> 非クラスター化列ストア インデックスを作成します。  
 非クラスター化列ストア インデックスにデータを読み込む最初にデータをヒープとして格納されている、またはクラスター化は、従来の行ストア テーブルを読み込み、インデックスを作成し、使用して[CREATE COLUMNSTORE INDEX &#40;TRANSACT-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql)を作成する、列ストア インデックスです。  
  
 ![列ストア インデックスにデータを読み込む](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "列ストア インデックスにデータを読み込む")  
  
##  <a name="change"></a> 非クラスター化列ストア インデックス内のデータを変更します。  
 テーブルに非クラスター化列ストア インデックスを作成すると、そのテーブル内のデータは変更できなくなります。 INSERT、UPDATE、DELETE、または MERGE を使用するクエリは失敗し、エラー メッセージが返されます。 テーブル内のデータを追加または変更するには、次のいずれかの操作を行います。  
  
-   列ストア インデックスを無効にします。 その後、テーブル内のデータを更新できます。 列ストア インデックスを無効にすると、データの更新の終了時に列ストア インデックスを再構築できます。 以下に例を示します。  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   列ストア インデックスを削除、テーブルを更新および列ストア インデックスの作成を列ストア インデックスを再作成します。 以下に例を示します。  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   列ストア インデックスのないステージング テーブルにデータを読み込みます。 ステージング テーブルで列ストア インデックスを構築します。 ステージング テーブルをメイン テーブルの空のパーティションに切り替えます。  
  
-   列ストア インデックスを持つテーブルから空のステージング テーブルにパーティションを切り替えます。 ステージング テーブルに列ストア インデックスがある場合は、列ストア インデックスを無効にします。 更新を実行します。 列ストア インデックスを構築 (または再構築) します。 ステージング テーブルを切り替えて、メイン テーブルの (空になった) パーティションに戻します。  
  

  
  
