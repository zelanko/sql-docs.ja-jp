---
title: Oracle のテーブルおよび列の選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af7f97d7d1671aada299b685981e81d62010df24
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788345"
---
# <a name="select-oracle-tables-and-columns"></a>Oracle のテーブルおよび列の選択
  [Oracle のテーブルおよび列の選択] ページを使用すると、変更をキャプチャする Oracle ソース データベースからテーブルを選択できます。 このページには次の要素があります。  
  
## <a name="options"></a>および  
 **テーブルの一覧**  
 テーブルの一覧には、次の 3 列が含まれています。  
  
-   **Oracle テーブル名**:テーブル スキーマを含む、テーブルの名前。  
  
-   **キャプチャ インスタンス**:名前のインスタンスに固有の変更データ キャプチャ オブジェクトに使用されるキャプチャ インスタンスの名前。 キャプチャ インスタンスは NULL にできません。  
  
     指定しない場合、ソース スキーマ名とソース テーブル名に基づき、 `<schema-name>_<table-name>`形式の名前が付けられます。 キャプチャ インスタンス名は 100 文字を超えることはできず、データベース内で一意である必要があります。  
  
     この列のセルをクリックすると、 **capture_instance**を手動で編集できます。  
  
-   **セキュリティ ロール**:ゲーティング ロールの変更データへのアクセスを制御するために使用するデータベースの名前。  
  
     この列のセルをクリックすると、 **security_role**を手動で編集できます。  
  
 **テーブルの追加**  
 **[テーブルの追加]** をクリックすると、 [変更をキャプチャするための Oracle テーブルの選択](select-oracle-tables-for-capturing-changes.md)を行うことができる [テーブル選択] ダイアログ ボックスが開きます。  
  
 **[編集]**  
 一覧からテーブルを選択して **[編集]** をクリックすると、そのテーブルの **[プロパティ]** ダイアログ ボックスが表示され、 [変更をキャプチャするために選択したテーブルに対する変更](make-changes-to-the-tables-selected-for-capturing-changes.md)を行うことができます。  
  
 **[削除]**  
 一覧からテーブルを選択して **[削除]** をクリックすると、CDC インスタンスからテーブルを削除できます。  
  
 適切なダイアログ ボックスを使用して [変更をキャプチャするための Oracle テーブルの選択](select-oracle-tables-for-capturing-changes.md) または [変更をキャプチャするために選択したテーブルに対する変更](make-changes-to-the-tables-selected-for-capturing-changes.md) を行った後、 **[次へ]** をクリックして [補足ログ スクリプトの生成および実行](generate-and-run-the-supplemental-logging-script.md)を行います。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md)   
 [テーブルの編集](edit-tables.md)   
 [CDC へのテーブルの追加](add-tables-to-a-cdc-instance.md)   
 [テーブルのプロパティの編集](edit-the-table-properties.md)  
  
  
