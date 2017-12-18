---
title: "パブリケーションでのアーティクルの追加および削除 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11733df97dc31d0fa6542ce27e44052f4fabfe5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>パブリケーションでのアーティクルの追加および削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] パブリケーションの新規作成ウィザードでパブリケーションを作成する場合は、最初にアーティクルを追加します。 このウィザードの使用の詳細については、「[パブリケーションの作成](../../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
 パブリケーションの作成後、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページでアーティクルを追加または削除します。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。 アーティクルの追加と削除に関する注意点については、「[既存のパブリケーションでのアーティクルの追加および削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>パブリケーションの作成後にアーティクルを追加するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、**[チェック ボックスがオンのオブジェクトのみ一覧に表示する]** チェック ボックスをオフにします。 これにより、パブリケーション データベース内のパブリッシュされていないオブジェクトも表示されるようになります。  
  
2.  追加する各アーティクルの隣にあるチェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>アーティクルを削除するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、削除するアーティクルの隣にあるチェック ボックスをオフにします。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [アーティクルの定義](../../../relational-databases/replication/publish/define-an-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
