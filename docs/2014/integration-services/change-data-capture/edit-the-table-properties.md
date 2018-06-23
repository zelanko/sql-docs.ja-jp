---
title: テーブルのプロパティの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1e63f11c9396107d7ab18743e69ec31c82276fdc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179370"
---
# <a name="edit-the-table-properties"></a>テーブルのプロパティの編集
  変更がキャプチャされている選択したテーブルの特定の列を編集するには、このダイアログ ボックスを使用します。 **[セキュリティ ロール]** と **[キャプチャ インスタンス]** の情報を編集することもできます。  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a>CDC インスタンスに含める列を編集するには  
  
1.  次のいずれかまたは両方の操作を行います。  
  
    -   CDC インスタンスに含める追加の列の横のチェック ボックスをオンにします。  
  
    -   CDC インスタンスに含めない列の横のチェック ボックスをオフにします。  
  
### <a name="to-edit-the-security-role"></a>セキュリティ ロールを編集するには  
  
1.  **"セキュリティ ロール"** フィールドで、新しい名前を入力するか、セキュリティ ロールの名前を編集します。  
  
### <a name="to-create-a-new-capture-instance"></a>新しいキャプチャ インスタンスを作成するには  
  
1.  **[セキュリティ ロール]** セクションの **"名前"** フィールドに、キャプチャ インスタンスの名前を入力します。 既定では、このフィールドに入力される名前は、現在のキャプチャ インスタンスの名前の末尾に **_NEW** を追加したものです (例: **old_instance_NEW**)。  
  
2.  キャプチャ インスタンスを次のいずれかとして保存します。  
  
    -   **[新しいキャプチャ インスタンス]**: この場合、新しいキャプチャ インスタンスが保存され、古いキャプチャ インスタンスは削除されません。  
  
         **注**: テーブルごとに 2 つまでのキャプチャ インスタンスを設定できます。 既に 2 つのキャプチャ インスタンスがある場合、このオプションは利用できません。  
  
    -   **[既存のものを置換]**: この場合、現在のキャプチャ インスタンスが削除され、作成したキャプチャ インスタンスで置換されます。 このテーブルに 2 つのキャプチャ インスタンスが定義されている場合、置換するキャプチャ インスタンスを選択する必要があります。  
  
 **注**: **[テーブル]** タブのテーブルの一覧からキャプチャ インスタンスを削除できます。  
  
 このダイアログ ボックスで情報の入力を終了したら、 **[OK]** をクリックして変更を受け入れます。  
  
## <a name="see-also"></a>参照  
 [CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md)   
 [変更をキャプチャするために選択したテーブルに対する変更](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  