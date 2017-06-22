---
title: "拡張イベント セッションの変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9330ef01cb491fef9307149e0cc774fa2b042c52
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="alter-an-extended-events-session"></a>拡張イベント セッションの変更
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

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
  
-   オブジェクト エクスプローラーで **[管理]**を展開し、 **[拡張イベント]**を展開して、 **[セッション]**を展開します。  
  
-   変更するセッションを右クリックし、 **[プロパティ]**をクリックします。  
  
-   **[プロパティ]** ダイアログ ボックスで、必要な変更を行い、 **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [クエリ エディターを使用した拡張イベント セッションの作成](http://msdn.microsoft.com/library/cba0e02b-b201-4863-bf1b-9164e68e5fa8)  
  
  
