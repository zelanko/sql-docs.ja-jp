---
title: '[全般] ([ストレージのオプション] ダイアログ ボックス) (Analysis Services - 多次元データ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d71e6c2ec49565c2db822d8bb96f26257ebf4f96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077227"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>[全般] ([ストレージのオプション] ダイアログ ボックス) (Analysis Services - 多次元データ)
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の **[ストレージのオプション]** ダイアログ ボックスの **[全般]** タブを使用すると、ディメンション、キューブ、メジャー グループ、またはパーティションにストレージ モードとプロアクティブ キャッシュを設定できます。  
  
> [!NOTE]  
>  これらの設定を変更する前に、ストレージ モードおよびプロアクティブ キャッシュの機能について理解しておく必要があります。 詳細については、「[プロアクティブ キャッシュ &#40;パーティション&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**ストレージ モード**|オブジェクトで使用するストレージ モードを選択します。<br /><br /> **MOLAP**<br /> 多次元 OLAP (MOLAP) ストレージが使用されます。<br /><br /> **HOLAP**<br /> ハイブリッド OLAP (HOLAP) ストレージが使用されます。<br /><br /> **ROLAP**<br /> リレーショナル OLAP (ROLAP) ストレージが使用されます。|  
|**プロアクティブ キャッシュを有効にします。**|プロアクティブ キャッシュを有効にします。<br /><br /> 注: このオプションが選択されていない場合、 **[ストレージ モード]** を除くすべてのオプションは無効です。|  
|**データが変更されたときに、キャッシュを更新します。**|**[通知]** タブで選択した通知方法を使用して、通知を受け取るたびにオブジェクトの MOLAP イメージを更新します。 **[通知]** タブの詳細については、「[[通知] &#40;[ストレージのオプション] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)」を参照してください。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。|  
|**サイレント状態の間隔**|プロアクティブ キャッシュによってオブジェクトに対する新しい MOLAP イメージの作成が開始される前に、オブジェクトが動作しない最短間隔と時間単位を設定します。<br /><br /> 注: このオプションは、 **[データの変更時にキャッシュを更新する]** が選択されていない場合は無効です。|  
|**サイレント状態のオーバーライド間隔**|現在のオブジェクトの利用状況にかかわらず、オブジェクトに対する通知の受信後、プロアクティブ キャッシュによってオブジェクトの新しい MOLAP イメージの作成が開始される最長間隔と時間単位を設定します。 この間隔に到達した後で受信した通知により、この間隔によってトリガーされた MOLAP イメージのプロセスが中止されることはありません。<br /><br /> 注: このオプションは、 **[データの変更時にキャッシュを更新する]** が選択されていない場合は無効です。 場合、このオプションを設定しない必要がありますが**ストレージ モード**に設定されている**HOLAP**です。|  
|**古いキャッシュを削除します。**|新しい MOLAP キャッシュの作成の開始と、既存の MOLAP キャッシュの削除までの間隔を指定します。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。 場合、このオプションを設定しない必要がありますが**ストレージ モード**HOLAP に設定します。|  
|**[待機時間]**|新しい MOLAP キャッシュの作成と、既存の MOLAP キャッシュの削除までの間隔と時間単位を選択します。<br /><br /> 注: このオプションは、 **[古いキャッシュを削除する]** が選択されていない場合は無効です。 場合、このオプションを設定しない必要がありますが**ストレージ モード**に設定されている**HOLAP**です。|  
|**キャッシュを定期的に更新します。**|通知にかかわらず、定期的に MOLAP イメージを更新します。<br /><br /> 注: このオプションは、 **[プロアクティブ キャッシュを有効にする]** が選択されていない場合は無効です。 場合、このオプションを設定しない必要がありますが**ストレージ モード**に設定されている**HOLAP**です。|  
|**再構築間隔**|新しい MOLAP イメージが作成された後、通知にかかわらず、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がオブジェクトに対して MOLAP イメージのプロセスを再開する間隔と時間単位を選択します。 この間隔に到達した後で受信した通知により、この間隔によってトリガーされた MOLAP イメージのプロセスが中止されることはありません。<br /><br /> 注: このオプションは、 **[キャッシュを定期的に更新]** が選択されていない場合は無効です。 場合、このオプションを設定しない必要がありますが**ストレージ モード**に設定されている**HOLAP**です。|  
|**すぐにオンラインします。**|オブジェクトをすぐにオンラインにします。 このオプションを設定した場合、オブジェクトは基になる ROLAP ストレージを使用して、MOLAP キャッシュが再構築される間にクエリを解決します。 このオプションが設定されていない場合、オブジェクトに対する MOLAP キャッシュが完了した後にのみ、オブジェクトがオンラインになります。|  
|**ROLAP 集計を有効にします。**|基になるデータ ソース上の具体化されたビューを使用して、集計を格納します。<br /><br /> 注: 基になるデータ ソースが具体化されたビューをサポートしない場合は、オブジェクトの処理時にエラーが発生します。|  
|**ディメンションに設定を適用します。**|関連するディメンションにストレージ モードとプロアクティブ キャッシュ設定を適用します。|  
  
## <a name="see-also"></a>参照  
 [記憶域のオプション ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [通知&#40;記憶域のオプション ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  