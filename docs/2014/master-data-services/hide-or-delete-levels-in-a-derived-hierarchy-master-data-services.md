---
title: 派生階層のレベルを非表示にするか削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 703e18130367c3d508cc6f40f4cdb9af17093f4e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088132"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>派生階層のレベルを非表示にするか削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、レベルを使用してグループ化する必要があるが、レベルを表示する必要はない場合は、派生階層のレベルを非表示にします。 グループ化にレベルを使用しない場合はレベルを削除します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>派生階層のレベルを非表示にするか削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **モデル ビュー**  ページで、ポイントして、メニュー バーから**管理** をクリック**派生階層**します。  
  
3.  **[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  編集する派生階層の列を選択します。  
  
5.  クリックして**派生階層の選択項目の編集**します。  
  
6.  **[現在のレベル]** ペインで、次のいずれかを実行します。  
  
    -   レベルを非表示にするには、最上位または最下位以外のレベルをクリックします。 **[表示]** ボックスの一覧で **[いいえ]** を選択します。 **[選択した階層アイテムの保存]** をクリックします。  
  
    -   最上位レベルを削除するには、 **[選択した階層アイテムの削除]** をクリックします。 確認のダイアログ ボックスで **[OK]** をクリックします。 削除できるのは最上位レベルだけです。  
  
## <a name="see-also"></a>参照  
 [階層内のメンバーを移動&#40;マスター データ サービス&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)   
 [派生階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
