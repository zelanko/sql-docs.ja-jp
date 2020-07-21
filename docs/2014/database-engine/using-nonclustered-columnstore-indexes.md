---
title: 非クラスター化列ストアインデックスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927773"
---
# <a name="using-nonclustered-columnstore-indexes"></a>非クラスター化列ストア インデックスの使用
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルの非クラスター化 columnstore インデックスを使用するキー タスクについて説明します。

 列ストアインデックスの概要については、「[列ストアインデックス](../relational-databases/indexes/columnstore-indexes-described.md)の概要」を参照してください。

 クラスター化列ストアインデックスの詳細については、「[クラスター化列ストアインデックスの使用](../relational-databases/indexes/indexes.md)」を参照してください。

## <a name="contents"></a>内容

-   [非クラスター化 Columnstore インデックスの作成](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [非クラスター化列ストアインデックスのデータを変更する](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a>非クラスター化列ストアインデックスを作成する
 データを非クラスター化列ストアインデックスに読み込むには、まず、ヒープまたはクラスター化インデックスとして格納されている従来の行ストアテーブルにデータを読み込み、次に[CREATE 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)を使用して列ストアインデックスを作成します。

 ![列ストア インデックスへのデータの読み込み](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "列ストア インデックスへのデータの読み込み")

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a>非クラスター化列ストアインデックスのデータを変更する
 テーブルに非クラスター化列ストア インデックスを作成すると、そのテーブル内のデータは変更できなくなります。 INSERT、UPDATE、DELETE、または MERGE を使用するクエリは失敗し、エラーメッセージが返されます。 そのテーブル内のデータを追加または変更するには、次のいずれかの操作を行います。

-   列ストアインデックスを無効にします。 その後、テーブル内のデータを更新できます。 列ストア インデックスを無効にした場合、データの更新の終了時に列ストア インデックスを再構築できます。 次に例を示します。

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   列ストアインデックスを削除し、テーブルを更新してから、CREATE 列ストアインデックスを使用して列ストアインデックスを再作成します。 次に例を示します。

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   列ストア インデックスのないステージング テーブルにデータを読み込みます。 そのステージング テーブルに列ストア インデックスを構築します。 そのステージング テーブルをメイン テーブルの空のパーティションに切り替えます。

-   列ストア インデックスを持つテーブルから空のステージング テーブルにパーティションを切り替えます。 ステージング テーブルに列ストア インデックスがある場合は、列ストア インデックスを無効にします。 更新を実行します。 列ストア インデックスを構築 (または再構築) します。 ステージング テーブルを切り替えて、メイン テーブルの (空になった) パーティションに戻します。




