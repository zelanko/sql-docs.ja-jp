---
title: 拡張イベント セッションのスクリプトを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71b9918e2f05efcc5a8720dcedeef023392f99ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085055"
---
# <a name="script-an-extended-event-session"></a>拡張イベント セッションのスクリプト化
  このトピックでは、イベント セッションをスクリプト化する方法について説明します。 イベント セッションはエクスポート、変更、または削除できるほか、イベント セッションを削除してから新たに作成し、次のような形式で出力することができます。  
  
-   **新しいクエリ エディター ウィンドウ**  
  
-   **[最近使ったファイル]**  
  
-   **クリップボード**  
  
-   **エージェント ジョブ**  
  
### <a name="to-script-an-existing-event-session"></a>既存のイベント セッションをスクリプト化するには  
  
1.  オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。  
  
2.  スクリプト化するセッションを右クリックし、 **[セッションをスクリプト化]** をポイントして **[CREATE]** をポイントした後、セッションのスクリプトをどこに出力するかを選択します。  
  
### <a name="to-script-a-new-event-session"></a>新しいイベント セッションをスクリプト化するには  
  
1.  オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。  
  
2.  **[セッション]** を右クリックし、 **[新しいセッション]** をクリックします。  
  
3.  **[新しいセッション]** の UI でイベント セッションを作成した後、イベント セッション スクリプトの出力先を **[スクリプト]** ボックスの一覧から選択します。  
  
### <a name="to-script-a-modified-event-session"></a>イベント セッションに変更を加えてスクリプト化するには  
  
1.  オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。  
  
2.  変更するセッションを右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[セッションのプロパティ]** ダイアログ ボックスでイベント セッションに変更を加えた後、その変更後のセッション スクリプトの出力先を **[スクリプト]** ボックスの一覧から選択します。  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../relational-databases/extended-events/extended-events.md)  
  
  