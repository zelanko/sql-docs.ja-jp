---
title: 準加法の動作の定義 (ビジネスインテリジェンスウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 161e2cb9dd9eeae4f2ed369b77ab0799ae12a33a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082001"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a>[準加法の動作の定義] (ビジネス インテリジェンス ウィザード)
  **[準加法の動作の定義]** ページを使用すると、メジャーに対する準加法の動作を有効または無効にできます。 準加法の動作によって、キューブに含まれるメジャーが時間ディメンションで集計される方法が決まります。  
  
> [!NOTE]  
>  Standard Edition で使用できる LastChild を除き、準加法の動作を使用できるのは、Business Intelligence または Enterprise Edition のみです。 さらに、準加法の動作はメジャーのみを対象にして定義するものであり、ディメンションを対象にしていないため、ディメンション デザイナーからビジネス インテリジェンス ウィザードを起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラー内にあるディメンションを右クリックした場合は、ウィザード内でこのページは表示されません。  
  
## <a name="options"></a>オプション  
 **[準加法の動作を無効にする]**  
 キューブに含まれるすべてのメジャーで準加法の動作を無効にします。  
  
 **準加法メンバーを含む\<ディメンション名> 勘定科目ディメンションが検出されました。サーバーは、勘定科目の種類ごとに指定された準加法の動作に従って、このディメンションのメンバーを集計します。**  
 準加法メンバーを含む勘定科目ディメンションの準加法の動作を有効にします。 このオプションを選択して、`ByAccount` への勘定科目ディメンションを参照する、メジャー グループのすべてのメジャーの集計関数を設定します。  
  
 勘定科目ディメンションの詳細については、「 [親子型ディメンションの財務アカウントの作成](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)」を参照してください。  
  
 **[個別のメジャーに準加法の動作を定義する]**  
 準加法の動作を有効にして、特定のメジャーに対して準加法集計関数を指定します。 集計関数は、メジャーを含むメジャー グループによって参照されるすべてのディメンションに対して適用されます。  
  
 **メジャー**  
 キューブに含まれるメジャーの名前を表示します。  
  
 **[集計関数]**  
 選択されたメジャーの集計関数を選択します。 次の表は、使用できる集計関数の一覧を示しています。  
  
|[値]|説明|  
|-----------|-----------------|  
|**AverageOfChildren**|メジャーの子の平均を返すことによって集計されます。|  
|`ByAccount`|勘定科目ディメンションで指定された属性の勘定科目の種類に関連付けられた集計関数によって集計されます。|  
|`Count`|`Count` 関数を使用して集計されます。|  
|`DistinctCount`|`DistinctCount` 関数を使用して集計されます。|  
|**FirstChild**|メジャーの最初の子メンバーを返すことによって時間ディメンションで集計されます。|  
|**FirstNonEmpty**|メジャーの最初の空でないメンバーを返すことによって時間ディメンションで集計されます。|  
|**LastChild**|メジャーの最後の子メンバーを返すことによって時間ディメンションで集計されます。|  
|**LastNonEmpty**|メジャーの最後の空でないメンバーを返すことによって時間ディメンションで集計されます。|  
|`Max`|`Max` 関数を使用して集計されます。|  
|`Min`|`Min` 関数を使用して集計されます。|  
|**なし**|集計は実行されません。|  
|`Sum`|`Sum` 関数を使用して集計されます。|  
  
> [!NOTE]  
>  このオプションの選択は、 **[個別のメジャーに準加法の動作を定義する]** が選択されている場合にのみ適用されます。  
  
## <a name="see-also"></a>参照  
 [ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md)   
 [キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
