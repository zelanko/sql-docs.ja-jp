---
title: '[全般] ([ストレージのオプション] ダイアログボックス) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
author: minewiskan
ms.author: owend
ms.openlocfilehash: f67e3f7a3c9d84c8095286707c3dd6ce2c22c3bd
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544407"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>[全般] ([ストレージのオプション] ダイアログ ボックス) (Analysis Services - 多次元データ)
  **の** [ストレージのオプション] **ダイアログ ボックスの** [全般] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] タブを使用すると、ディメンション、キューブ、メジャー グループ、またはパーティションにストレージ モードとプロアクティブ キャッシュを設定できます。  
  
> [!NOTE]  
>  これらの設定を変更する前に、ストレージ モードおよびプロアクティブ キャッシュの機能について理解しておく必要があります。 詳細については、「[プロアクティブ キャッシュ (パーティション)](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**ストレージモード**|オブジェクトで使用するストレージ モードを選択します。<br /><br /> **[MOLAP]**<br /> 多次元 OLAP (MOLAP) ストレージが使用されます。<br /><br /> **HOLAP**<br /> ハイブリッド OLAP (HOLAP) ストレージが使用されます。<br /><br /> **[ROLAP]**<br /> リレーショナル OLAP (ROLAP) ストレージが使用されます。|  
|**プロアクティブ キャッシュを有効にします。**|プロアクティブ キャッシュを有効にします。<br /><br /> 注: このオプションが選択されていない場合、 **[ストレージ モード]** を除くすべてのオプションは無効です。|  
|**[データの変更時にキャッシュを更新する]**|**[通知]** タブで選択した通知方法を使用して、通知を受け取るたびにオブジェクトの MOLAP イメージを更新します。 **[通知]** タブの詳細については、「[[通知] &#40;[ストレージのオプション] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)」を参照してください。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。|  
|**[サイレント状態の間隔]**|プロアクティブ キャッシュによってオブジェクトに対する新しい MOLAP イメージの作成が開始される前に、オブジェクトが動作しない最短間隔と時間単位を設定します。<br /><br /> 注: このオプションは、 **[データの変更時にキャッシュを更新する]** が選択されていない場合は無効です。|  
|**[サイレント状態のオーバーライド間隔]**|現在のオブジェクトの利用状況にかかわらず、オブジェクトに対する通知の受信後、プロアクティブ キャッシュによってオブジェクトの新しい MOLAP イメージの作成が開始される最長間隔と時間単位を設定します。 この間隔に到達した後で受信した通知により、この間隔によってトリガーされた MOLAP イメージのプロセスが中止されることはありません。<br /><br /> 注: このオプションは、 **[データの変更時にキャッシュを更新する]** が選択されていない場合は無効です。 また、[**ストレージモード**] が [ **HOLAP**] に設定されている場合は、このオプションを設定しないでください。|  
|**[古いキャッシュを削除する]**|新しい MOLAP キャッシュの作成の開始と、既存の MOLAP キャッシュの削除までの間隔を指定します。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。 また、[**ストレージモード**] が [HOLAP] に設定されている場合は、このオプションを設定しないでください。|  
|**待機時間**|新しい MOLAP キャッシュの作成と、既存の MOLAP キャッシュの削除までの間隔と時間単位を選択します。<br /><br /> 注: このオプションは、 **[古いキャッシュを削除する]** が選択されていない場合は無効です。 また、[**ストレージモード**] が [ **HOLAP**] に設定されている場合は、このオプションを設定しないでください。|  
|**[キャッシュを定期的に更新する]**|通知にかかわらず、定期的に MOLAP イメージを更新します。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。 また、[**ストレージモード**] が [ **HOLAP**] に設定されている場合は、このオプションを設定しないでください。|  
|**[再構築間隔]**|新しい molap イメージが作成された後、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 通知に関係なく、オブジェクトに対して molap イメージのプロセスを再開する間隔と時間単位を選択します。 この間隔に到達した後で受信した通知により、この間隔によってトリガーされた MOLAP イメージのプロセスが中止されることはありません。<br /><br /> 注: このオプションは、 **[キャッシュを定期的に更新]** が選択されていない場合は無効です。 また、[**ストレージモード**] が [ **HOLAP**] に設定されている場合は、このオプションを設定しないでください。|  
|**[すぐにオンラインにする]**|オブジェクトをすぐにオンラインにします。 このオプションを設定した場合、オブジェクトは基になる ROLAP ストレージを使用して、MOLAP キャッシュが再構築される間にクエリを解決します。 このオプションが設定されていない場合、オブジェクトに対する MOLAP キャッシュが完了した後にのみ、オブジェクトがオンラインになります。|  
|**[ROLAP 集計を有効にする]**|基になるデータ ソース上の具体化されたビューを使用して、集計を格納します。<br /><br /> 注: 基になるデータ ソースが具体化されたビューをサポートしない場合は、オブジェクトの処理時にエラーが発生します。|  
|**[設定をディメンションに適用する]**|関連するディメンションにストレージ モードとプロアクティブ キャッシュ設定を適用します。|  
  
## <a name="see-also"></a>参照  
 [[ストレージのオプション] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [[通知 &#40;ストレージのオプション] ダイアログボックス&#41; &#40;Analysis Services-多次元データ&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  
