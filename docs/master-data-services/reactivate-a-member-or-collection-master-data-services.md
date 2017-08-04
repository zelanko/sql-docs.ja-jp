---
title: "メンバーまたはコレクション (Master Data Services) を再アクティブ化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
caps.latest.revision: 11
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc90708210730332fc2baafa0f6ab61ceadb6840
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="reactivate-a-member-or-collection-master-data-services"></a>メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、次のいずれかの状態にあったメンバーを再アクティブ化できます。  
  
-   ステージング処理によって非アクティブにされた。  
  
-   MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]で削除された。  
  
-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで削除された。  
  
 メンバーを再アクティブ化すると、階層およびコレクションのメンバーの属性とメンバーシップが復元されます。  
  
 また、コレクションを再アクティブ化することもできます。 その場合、コレクションの属性と、コレクションに属するメンバーが復元されます。  
  
 メンバーまたはコレクションを再アクティブ化すると、以前のトランザクションがすべて復元されます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]の **[バージョン管理]** 機能領域に対する権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-reactivate-a-member-or-collection"></a>メンバーまたはコレクションを再アクティブ化するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]**をクリックします。  
  
2.  メニュー バーの **[トランザクション]**をクリックします。  
  
3.  **[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
5.  **[トランザクション]** ペインで、再アクティブ化するメンバーまたはコレクションの行をクリックします。 この行の **[以前の値]** 列に **[アクティブ]** 、 **[新しい値]** 列に **[非アクティブ]** と表示されます。  
  
6.  **[トランザクションの破棄]**をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]**をクリックします。 **[新しい値]** 列に **[アクティブ]** と表示され、新しいトランザクションが追加されます。  
  
## <a name="see-also"></a>参照  
 [メンバーまたはコレクションを削除する (マスター データ サービス)](../master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [メンバーと #40 です。マスター データ サービス &#41;](../master-data-services/members-master-data-services.md)   
 [コレクション & #40 です。マスター データ サービス &#41;](../master-data-services/collections-master-data-services.md)  
  
  

