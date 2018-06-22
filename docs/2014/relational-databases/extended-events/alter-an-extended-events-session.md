---
title: 拡張イベント セッションの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97971c56e6f094d7cf905da0db4475f3703c1416
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075966"
---
# <a name="alter-an-extended-events-session"></a>拡張イベント セッションの変更
  拡張イベント セッションを作成したら、 **SQL Server 拡張イベント ウィザード**を使用して、必要に応じて拡張イベント セッションを変更できます。  
  
## <a name="before-you-begin"></a>作業を開始する準備  
 アクティブなセッションおよび非アクティブなセッションのターゲットを変更することはできません。また、アクティブなセッションの詳細プロパティの構成を変更することはできません。  
  
 アクティブなイベント セッションと非アクティブなイベント セッションの両方に対して、次の変更を実行できます。  
  
-   セッションのイベントの追加または削除、および、イベントの構成 (イベントのフィールド、フィルター、アクションなど) の変更。  
  
-   イベント セッションのターゲットの追加または削除。  
  
-   **[サーバーの起動時にイベント セッションを開始する]** オプションの有効化。  
  
 非アクティブなイベント セッションに対しては、次の変更も実行できます。  
  
-   **[イベント間のリレーションシップの追跡]** オプションの有効化。  
  
-   詳細プロパティの構成の変更。  
  
> [!NOTE]  
>  **SQL Server 拡張イベント ウィザード** では、イベント セッションの変更はサポートされていません。  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>SQL Server 拡張イベント ウィザードを使用して拡張イベント セッションを変更する方法  
  
-   オブジェクト エクスプローラーで **[管理]** を展開し、 **[拡張イベント]** を展開して、 **[セッション]** を展開します。  
  
-   変更するセッションを右クリックし、 **[プロパティ]** をクリックします。  
  
-   **[プロパティ]** ダイアログ ボックスで、必要な変更を行い、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [クエリ エディターを使用した拡張イベント セッションの作成](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
