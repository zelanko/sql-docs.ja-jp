---
title: "\"既定でオフ\" ポリシーの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ad1ef04caea4fc15cc53fced05ab5861d54ad7eb
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-1-1---create-the-off-by-default-policy"></a>レッスン 1-1 - "既定でオフ" ポリシーの作成
ここでは、セキュリティ構成ファセットに基づく "メールをオフ" という条件を作成します。 その後、"既定でオフ" というポリシーを作成します。  
  
### <a name="to-create-the-mail-off-condition"></a>"メールをオフ" 条件を作成するには  
  
1.  オブジェクト エクスプローラーで、 **[管理]**、 **[ポリシー管理]**、 **[ファセット]**の順に展開し、 **[セキュリティ構成]**を右クリックして **[新しい条件]**をクリックします。  
  
2.  **[新しい条件の作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **メールをオフ**」と入力します。  
  
3.  **[ファセット]** ボックスで、 **[セキュリティ構成]** ファセットが選択されていることを確認します。  
  
4.  **[式]** 領域の **[フィールド]** ボックスで **@DatabaseMailEnabled** を選択し、**[演算子]** ボックスで **=** を選択し、**[値]** ボックスで **[False]** を選択します。  
  
5.  **[説明]** ページで条件の説明を入力し、 **[OK]** をクリックして条件を作成します。  
  
### <a name="to-create-the-off-by-default-policy"></a>"既定でオフ" ポリシーを作成するには  
  
1.  オブジェクト エクスプローラーで、 **[セキュリティ構成]**を右クリックし、 **[新しいポリシー]**をクリックします。  
  
2.  **[新しいポリシーの作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **既定でオフ**」と入力します。  
  
3.  **[有効]** チェック ボックスはオフのままにします。 **[有効]** チェック ボックスは自動ポリシーに適用され、このポリシーは要求時に実行されます。  
  
4.  **[条件の確認]** チェック ボックスを下にスクロールして **[セキュリティ構成]** 領域を表示し、確認する条件として **[メールをオフ]** を選択します。  
  
5.  サーバー スコープのポリシーなので、 **[対象]** ボックスは空白になります。  
  
6.  **[評価モード]** チェック ボックスで、 **[要求時]** を評価モードとして選択します。  
  
7.  **[サーバーの制限]** チェック ボックスで **[なし]**を選択します。  
  
8.  **[説明]** ページでポリシーの説明を入力します。  
  
9. **[追加のヘルプ ハイパーリンク]** 領域で、ポリシーの Web ページへのハイパーリンクを指定できます。 **[表示するテキスト]** ボックスに、ハイパーリンクに表示するテキストを入力します。  
  
10. **[アドレス]** ボックスに、会社の IT 部門のホーム ページなどのヘルプ ページへのハイパーリンクを入力します。  
  
11. Web ページを開いてアドレスを確認するには、 **[リンクのテスト]**をクリックします。  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
["既定でオフ" ポリシーを実行するためのサーバーの構成](../../relational-databases/policy-based-management/lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
  

