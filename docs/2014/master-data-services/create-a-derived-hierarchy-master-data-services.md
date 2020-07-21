---
title: 派生階層を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7c831ab360f2cbe4b32834ae2a280b961d2bac1e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971872"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>派生階層を作成する (マスター データ サービス)
  正しいレベルにメンバーが確実に存在するレベル ベースの階層が必要な場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、派生階層を作成します。 派生階層は、モデル内に存在するドメイン ベースの属性のリレーションシップに基づきます。  
  
> [!NOTE]  
>  ドメイン ベースの属性値がメンバーに対して存在しない場合、メンバーは派生階層に含まれません。 すべてのメンバーのドメイン ベースの属性値を要求するには、「[属性値を要求する (マスター データ サービス)](require-attribute-values-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-create-a-derived-hierarchy"></a>派生階層を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  [**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**派生階層**] をクリックします。  
  
3.  **[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  [**派生階層の追加**] をクリックします。  
  
5.  **[派生階層の追加]** ページの **[派生階層名]** ボックスに階層の名前を入力します。  
  
    > [!TIP]  
    >  名前は、たとえば **"カテゴリに含まれるサブカテゴリに含まれる製品"** のように、階層のレベルがわかる形式にします。  
  
6.  **[派生階層の保存]** をクリックします。  
  
7.  [**派生階層の編集**] ページの [**使用できるエンティティと階層**] ペインで、エンティティまたは階層をクリックし、[**現在のレベル**] ペインにドラッグします。  
  
8.  その他のエンティティまたは階層をドラッグして、階層を完成させます。  
  
9. **[戻る]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [明示的なキャップを持つ派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [ドメインベースの属性 (マスター データ サービス)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
