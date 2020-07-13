---
title: '[ストレージの設定] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.f1
- sql12.asvs.cubeeditor.cubebuilder.measuregroupstoragesettings.f1
ms.assetid: 80c41c71-226c-45fe-b9cf-af824b592fe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: dc3e6d627bf7e3072d8b6ff40a644773474ba4cb
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940230"
---
# <a name="storage-settings-dialog-box-analysis-services---multidimensional-data"></a>[ストレージ設定] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [ストレージ設定] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、ディメンション、キューブ、メジャー グループ、およびパーティションのプロアクティブ キャッシュ、ストレージ、および通知設定を指定できます。 **で** [ストレージ設定] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを表示するには、次の手順に従います。  
  
-   **...** `ProactiveCaching` の [**プロパティ**] ウィンドウで、ディメンション、キューブ、メジャーグループ、またはパーティションのプロパティ値の省略記号ボタン ([...]) をクリックし [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。  
  
-   **キューブ デザイナー** の **[パーティション]** タブでメジャー グループを展開し、 **[ストレージ設定]** をクリックします。  
  
-   **キューブ デザイナー** の **[パーティション]** タブで、メジャー グループを展開し、メジャー グループのグリッド内でパーティションを選択します。次に、 **[ストレージ設定]** をクリックします。  
  
-   **キューブ デザイナー** の **[パーティション]** タブで、メジャー グループを展開し、メジャー グループのグリッド内でパーティションを選択します。次に、 **キューブ デザイナー** の **[パーティション]** タブの **ツール バー** 上にある、 **[ストレージ設定]** をクリックします。  
  
## <a name="options"></a>オプション  
  
|期間|定義|値|  
|----------|----------------|------------|  
|**[標準設定]**|**標準設定のスライダー** を有効にして、ストレージ モードとプロアクティブ キャッシュ機能で、定義済みの設定を使用します。||  
|**標準設定のスライダー**|次の定義済み設定のいずれかに設定します。<br /><br /> **[リアルタイム ROLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|ROLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 0 秒で削除します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
||**[リアルタイム HOLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|HOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 0 秒で削除します。<br /><br /> データが変更されると、アクティビティがない状態の間隔 0 秒、アクティビティがない状態のオーバーライド間隔なしでキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
||**[低待機時間 MOLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 30 分で削除します。<br /><br /> アクティビティがない状態の間隔 10 秒、アクティビティがない状態のオーバーライド間隔 10 分でキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
||**[中待機時間 MOLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 4 時間で削除します。<br /><br /> アクティビティがない状態の間隔 10 秒、アクティビティがない状態のオーバーライド間隔 10 分でキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
||**自動 MOLAP**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> データが変更されると、アクティビティがない状態の間隔 0 秒、アクティビティがない状態のオーバーライド間隔なしでキャッシュを更新します。|  
||**[定期 MOLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> キャッシュを定期的に更新します。再構築間隔は 1 日です。|  
||**[MOLAP]**<br /><br /> 次のストレージとプロアクティブ キャッシュ設定を使用します。|MOLAP ストレージ モードに設定します。|  
|**[カスタム設定]**|ストレージ モード、プロアクティブ キャッシュ、通知の各オプションを明示的に設定します。||  
|**Options**|**[ストレージのオプション]** ダイアログ ボックスを表示し、ストレージ モード、プロアクティブ キャッシュ、通知の各オプションを明示的に設定します。 **[ストレージ設定]** ダイアログ ボックスの詳細については、「[[ストレージ設定] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。||  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [&#40;パーティションのプロアクティブキャッシュ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Cube Storage &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)  
  
  
