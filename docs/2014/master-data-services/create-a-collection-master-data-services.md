---
title: コレクションを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4a278341b6ce997a6bad9b84e8e411d719c09c85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174200"
---
# <a name="create-a-collection-master-data-services"></a>コレクションを作成する (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、リーフ メンバーまたは統合メンバーの一覧表示を作成する必要があるときは、コレクションを作成します。 コレクションは、エンティティのすべてのメンバーを含む必要はありません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   エンティティのコレクション モデル オブジェクトに対して **更新** 権限が最低限必要です。  
  
-   エンティティは、明示的階層およびコレクションに対して有効化されている必要があります。 詳細については、次を参照してください。[明示的階層およびコレクションに対してエンティティを有効にする&#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)です。  
  
### <a name="to-create-a-collection"></a>コレクションを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
2.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
3.  **[エクスプローラー]** をクリックします。  
  
4.  メニュー バーの **[コレクション]** をポイントして、[ *entity_name*] をクリックします。  
  
5.  **[コレクションの追加]** をクリックします。  
  
6.  **[詳細]** タブの **[名前]** ボックスにコレクションの名前を入力します。  
  
7.  **[コード]** ボックスにコレクションの一意のコードを入力します。  
  
8.  必要に応じて、 **[説明]** ボックスにコレクションの説明を入力します。  
  
9. **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [コレクションにメンバーを追加&#40;マスター データ サービス&#41;](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;マスター データ サービス&#41;](../../2014/master-data-services/collections-master-data-services.md)   
 [メンバーまたはコレクションの削除&#40;マスター データ サービス&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [明示的階層を作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  