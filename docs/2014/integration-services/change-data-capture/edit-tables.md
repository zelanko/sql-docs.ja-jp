---
title: テーブルの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 264d288881d7996ee52bd28aa841be8948dfe56e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84923303"
---
# <a name="edit-tables"></a>テーブルの編集
  Oracle ソース データベースから選択したテーブルおよび列を変更するには、 **[テーブル]** タブを使用します。 このタブには次の要素があります。  
  
 **テーブルの一覧**  
 テーブルの一覧には、次の 3 列が含まれています。  
  
-   **[Oracle テーブル名]** : テーブル スキーマを含むテーブルの名前です。  
  
-   **[キャプチャ インスタンス]** : インスタンス固有の変更データ キャプチャ オブジェクトを識別するために使用されるキャプチャ インスタンスの名前です。 キャプチャ インスタンスは NULL にできません。 指定しなかった場合、ソース スキーマ名とソース テーブル名に基づいて、 `<schema-name>_<table-name>.` 形式の名前が付けられます。キャプチャ インスタンスの名前に指定できる文字数の上限は 100 文字です。また、データベース内で一意であることが必要です。 この列のセルをクリックすると、 **capture_instance**を手動で編集できます。  
  
-   **[セキュリティ ロール]** : 変更データへのアクセスの取得に使用するデータベース ロールの名前です。 この列のセルをクリックすると、 **security_role**を手動で編集できます。  
  
 **テーブルの追加**  
 **[テーブルの追加]** をクリックすると、 [CDC へのテーブルの追加](add-tables-to-a-cdc-instance.md)を行うことができる [テーブル選択] ダイアログ ボックスが開きます。 このセッションが Oracle データベースへの初回のアクセスである場合、 [Connect to Oracle](connect-to-oracle.md)を行う必要があります。  
  
 **[編集]**  
 一覧からテーブルを選択して **[編集]** をクリックすると、そのテーブルの **[プロパティ]** ダイアログ ボックスが表示され、 [テーブルのプロパティの編集](edit-the-table-properties.md)を行うことができます。  
  
> [!NOTE]  
>  既にミラー テーブルがあるテーブルの型マッピングは編集できません。 型マッピングは新しいテーブルに対してのみ行うことができます。  
  
 **Remove**  
 一覧からテーブルを選択して **[削除]** をクリックすると、CDC インスタンスからテーブルを削除できます。  
  
## <a name="see-also"></a>参照  
 [CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md)   
 [Oracle のテーブルおよび列の選択](select-oracle-tables-and-columns.md)  
  
  
