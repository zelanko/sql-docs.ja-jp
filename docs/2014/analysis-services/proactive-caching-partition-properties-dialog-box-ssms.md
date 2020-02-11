---
title: '[プロアクティブキャッシュ] ([パーティションのプロパティ] ダイアログボックス) (SSMS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.proactivecaching.f1
ms.assetid: ecba72a3-703f-4ede-9d85-9a3318a749e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb486ec383ab6fa1684bd9d0e9b8f6bc67631eee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070712"
---
# <a name="proactive-caching-partition-properties-dialog-box-ssms"></a>[プロアクティブ キャッシュ] ([パーティションのプロパティ] ダイアログ ボックス) (SSMS)
  SQL Server Management Studio の **[パーティションのプロパティ]** ダイアログ ボックスの **[プロアクティブ キャッシュ]** ページでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのキューブに対してメジャー グループのパーティションのストレージおよびプロアクティブ キャッシュのプロパティを設定できます。  
  
## <a name="options"></a>オプション  
 **[標準設定]**  
 
  **標準設定のスライダー** を有効にして、ストレージ モードとプロアクティブ キャッシュ機能で、定義済みの設定を使用します。  
  
 **標準設定のスライダー**  
 次の表に示されている定義済み設定のいずれかを設定します。  
  
|設定|[説明]|  
|-------------|-----------------|  
|**[リアルタイム ROLAP]**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> ROLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 0 秒で削除します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
|**[リアルタイム HOLAP]**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> HOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 0 秒で削除します。<br /><br /> データが変更されると、アクティビティがない状態の間隔 0 秒、アクティビティがない状態のオーバーライド間隔なしでキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
|**[低待機時間 MOLAP]**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 30 分で削除します。<br /><br /> アクティビティがない状態の間隔 10 秒、アクティビティがない状態のオーバーライド間隔 10 分でキャッシュを更新します。<br /><br /> アクティビティがない状態の間隔 10 秒、アクティビティがない状態のオーバーライド間隔 10 分でキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
|**[中待機時間 MOLAP]**|このチェックボックスをオンにすると、オブジェクトは直ちにオンラインになります。<br /><br /> ストレージとプロアクティブキャッシュの設定は次のとおりです。<br /><br /> MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> 古くなったキャッシュを待機時間 4 時間で削除します。<br /><br /> アクティビティがない状態の間隔 10 秒、アクティビティがない状態のオーバーライド間隔 10 分でキャッシュを更新します。<br /><br /> オブジェクトを直ちにオンラインにします。|  
|**自動 MOLAP**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> データが変更されると、アクティビティがない状態の間隔 0 秒、アクティビティがない状態のオーバーライド間隔なしでキャッシュを更新します。|  
|**[定期 MOLAP]**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> MOLAP ストレージ モードに設定します。<br /><br /> プロアクティブ キャッシュを有効にします。<br /><br /> キャッシュを定期的に更新します。再構築間隔は 1 日です。|  
|**MOLAP**|次のストレージとプロアクティブ キャッシュ設定を使用します。<br /><br /> MOLAP ストレージ モードに設定します。|  
  
 **[カスタム設定]**  
 ストレージ モード、プロアクティブ キャッシュ、通知の各オプションを明示的に設定します。  
  
 **オプション**  
 
  **[ストレージのオプション]** ダイアログ ボックスを表示し、ストレージ モード、プロアクティブ キャッシュ、通知の各オプションを明示的に設定します。 
  **[ストレージ設定]** ダイアログ ボックスの詳細については、「[[ストレージ設定] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [&#40;パーティションのプロアクティブキャッシュ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [[パーティションのプロパティ] ダイアログボックス &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [[選択 &#40;[パーティションのプロパティ] ダイアログボックス&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [[全般 &#40;[パーティションのプロパティ] ダイアログボックス&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)   
 [SSAS-多次元&#41;&#40;キューブ、パーティション、およびディメンションの処理のエラー構成](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
