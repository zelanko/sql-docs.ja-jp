---
title: 明示的階層を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08770818215b1055f2f5a015a696979bcea74f69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070733"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>明示的階層を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になった明示的階層を削除します。  
  
> [!WARNING]  
>  明示的階層を削除すると、階層内の統合メンバーもすべて削除されます。 エンティティに対する明示的階層を削除すると、エンティティのコレクションもすべて削除され、明示的階層およびコレクションに対してエンティティが無効になります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-an-explicit-hierarchy"></a>明示的階層を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  削除する明示的階層を含むエンティティの行を選択します。  
  
5.  **[選択したエンティティの編集]** をクリックします。  
  
6.  **エンティティの編集** ページの 、**明示的階層** ウィンドウで、削除する明示的階層をクリックします。  
  
7.  をクリックして**選択した階層を削除**です。  
  
8.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
9. 追加の確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [明示的階層を作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [明示的階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  