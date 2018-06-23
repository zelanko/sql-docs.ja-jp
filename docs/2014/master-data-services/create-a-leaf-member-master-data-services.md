---
title: リーフ メンバーを作成する (マスター データ サービス) | Microsoft Docs
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
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8db1358fc13310c56b6486af73eed694e8423cc2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179342"
---
# <a name="create-a-leaf-member-master-data-services"></a>リーフ メンバーを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]、マスター データをシステムに追加するステージング テーブルを使用していない場合は、リーフ メンバーを作成または[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]データをインポートします。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   最小値を持つ必要があります**更新**にメンバーを追加するエンティティのリーフ モデル オブジェクトに対する権限。  
  
### <a name="to-create-a-leaf-member"></a>リーフ メンバーを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
2.  ユーザーの場合は、 **[バージョン]** ボックスの一覧から未処理のバージョンを選択します。 管理者の場合は、 **[バージョン]** ボックスの一覧から、状態が未処理またはロック済みのバージョンを選択します。  
  
3.  **[エクスプローラー]** をクリックします。  
  
4.  メニュー バーの **[エンティティ]** をポイントして、メンバーを追加するエンティティの名前をクリックします。  
  
5.  **[メンバーの追加]** をクリックします。  
  
6.  **[詳細]** ペインのフィールドに入力します。  
  
7.  任意。 **[注釈]** ボックスに、メンバーを追加した理由についてのコメントを入力します。 そのメンバーにアクセスできるすべてのユーザーが、その注釈を表示できます。  
  
8.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [読み込むか、ステージング処理を使用してマスター データ サービス内のメンバーを更新します。](add-update-and-delete-data-master-data-services.md)   
 [統合メンバーを作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)   
 [メンバー&#40;マスター データ サービス&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
  