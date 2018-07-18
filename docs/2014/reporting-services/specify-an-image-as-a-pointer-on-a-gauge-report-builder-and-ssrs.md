---
title: 画像 (レポート ビルダーおよび SSRS) のゲージのポインターとして指定する |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
caps.latest.revision: 7
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d96efa70219c841abae8d0129716810645d283d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230145"
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
  
2.  (省略可能)ゲージにポインターが存在しない場合は、ゲージを選択します右クリックして**ポインターの追加**します。 ポインターがゲージに追加されます。  
  
3.  をクリックして、**挿入**リボンのタブし、[イメージ] アイコンをダブルクリックします。 **[画像のプロパティ]** ダイアログ ボックスが表示されます。  
  
4.  画像をレポートに追加します。 詳細については、次を参照してください。[レポートに画像を埋め込む&#40;レポート ビルダーおよび SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)します。  
  
5.  プロパティ ペインを開きます。  
  
6.  デザイン画面で、ポインターをクリックします。 ポインターのプロパティがプロパティ ペインに表示されます。  
  
7.  PointerImage ノードを展開します。  
  
8.  **ソース**、**埋め込み**ドロップダウン リストから。  
  
    > [!NOTE]  
    >  画像がデータベースまたは Web に保存されている場合は、このプロパティに適切なオプションを指定できます。 詳細については、次を参照してください。[イメージのプロパティ] ダイアログ ボックスの [全般]&#40;レポート ビルダーおよび SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)します。  
  
9. **値**、ドロップダウン リストから、イメージの名前を選択します。  
  
10. **TransparentColor**、イメージから削除する色の値を選択します。 これで、ゲージのポインターのシームレスな外観が作成されます。  
  
## <a name="see-also"></a>参照  
 [ゲージのポインターの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [レポートにゲージを追加&#40;レポート ビルダーおよび SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [線、色、および画像の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [ゲージ (レポート ビルダーおよび SSRS)](report-design/gauges-report-builder-and-ssrs.md)  
  
  
