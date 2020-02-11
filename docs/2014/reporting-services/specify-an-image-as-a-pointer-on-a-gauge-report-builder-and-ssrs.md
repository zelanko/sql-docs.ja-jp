---
title: 画像をゲージのポインターとして指定する (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7a57987a5d1cd0ac7984db3b716521d9c7a09af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101147"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a>画像をゲージのポインターとして指定する (レポート ビルダーおよび SSRS)
  ゲージには 3 つの組み込みスタイルが用意されており、これらを使用してポインターの外観をカスタマイズできます。 放射状ゲージには、針、マーカー、およびバーの 3 種類の組み込みスタイルがあります。 線形ゲージには、マーカー、バー、および温度計の 3 種類の組み込みスタイルがあります。 独自のポインターが必要な場合は、自分で作成した画像をポインターとして使用できます。  
  
 ポインターの画像を指定する場合、その画像は次の仕様を満たしている必要があります。  
  
-   ポインターの原点または回転の中心は、画像の上部にある必要があります。  
  
-   ポインターの端は下向きである必要があります。  
  
 ポインターは不規則な形状なので、画像の不必要な部分を隠すために透過色を指定する必要があります。 指定した色はゲージ上で表示されないので、通常はゲージ上に使用されない色を透過色として使用してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a>画像をゲージのポインターとして指定するには  
  
1.  [デザイン] ビューでゲージのポインターをクリックします。  
  
2.  Optionalゲージにポインターが存在しない場合は、ゲージを右クリックし、[**ポインターの追加**] を選択します。 ポインターがゲージに追加されます。  
  
3.  リボンの [**挿入**] タブをクリックし、[イメージ] アイコンをダブルクリックします。 
  **[画像のプロパティ]** ダイアログ ボックスが表示されます。  
  
4.  画像をレポートに追加します。 詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;に画像を埋め込む](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
5.  プロパティ ペインを開きます。  
  
6.  デザイン画面で、ポインターをクリックします。 ポインターのプロパティがプロパティ ペインに表示されます。  
  
7.  [ポインターイメージ] ノードを展開します。  
  
8.  [**ソース**] で、ドロップダウンリストから [**埋め込み**] を選択します。  
  
    > [!NOTE]  
    >  画像がデータベースまたは Web に保存されている場合は、このプロパティに適切なオプションを指定できます。 詳細については、「 [[画像のプロパティ] ダイアログボックス」、「全般 &#40;レポートビルダー」、および「SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)」を参照してください。  
  
9. [**値**] で、ドロップダウンリストから画像の名前を選択します。  
  
10. **TransparentColor**で、画像から削除する色の値を選択します。 これで、ゲージのポインターのシームレスな外観が作成されます。  
  
## <a name="see-also"></a>参照  
 [ゲージのポインターの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [ゲージをレポートに追加する &#40;レポートビルダーと SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [線、色、および画像の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [ゲージ (レポート ビルダーおよび SSRS)](report-design/gauges-report-builder-and-ssrs.md)  
  
  
