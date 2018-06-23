---
title: 対話的な並べ替え、ドキュメント マップ、およびリンク (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc6ef408-4a76-408a-9d3f-033481fe21cf
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3646edb01f7bf6e45bbe20c1e6f821b41e9b5969
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165736"
---
# <a name="interactive-sort-document-maps-and-links-report-builder-and-ssrs"></a>対話的な並べ替え、ドキュメント マップ、およびリンク (レポート ビルダーおよび SSRS)
  Web ベースの環境では、ユーザーがレポートと対話できるようにするさまざまな機能を追加できます。 ユーザーは、レポート内の値の並べ替え順序を変更したり、レポート内のアイテムの表示と非表示を切り替えたり、リンクをクリックして他のレポートや Web ページを表示したりできます。 また、目次やドキュメント マップを追加することもできます。 レポート ユーザーは、目次またはドキュメント マップ内のアイテムをクリックして、レポート内の領域に直接移動できます。  
  
 レポート ビルダーおよびレポート デザイナーでは、次のアクションが設定された 3 種類のリンクがサポートされています。  
  
-   **ブックマーク リンク** 同じレポート内の他の領域に移動します。  
  
-   **ハイパーリンク** URL アクセスを使用して Web ページのアドレスまたはレポート サーバー上のレポートを指定する URL に移動します。  
  
-   **詳細レポート リンク** 同じレポート サーバー上にあるその他のレポートに移動します。 詳細については、「[詳細レポート &#40;レポート ビルダーおよび SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  データセット フィールドにバインドされているリンクは、悪意的な改ざんに対して脆弱である可能性があります。 詳細については、msdn.microsoft.com で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?LinkId=154888)の「[レポートとリソースの保護](../security/secure-reports-and-resources.md)」を参照してください。  
  
 また、並べ替え、フィルター、表示などのパラメーター参照を含む式を作成すると、ユーザーがレポートの表示や内容を制御できるようになります。 詳細については、「[レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](report-parameters-report-builder-and-report-designer.md)」、「[データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)」、および「[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>このセクションの内容  
 [対話的な並べ替え&#40;レポート ビルダーおよび SSRS&#41;](interactive-sort-report-builder-and-ssrs.md)  
 対話型の並べ替えボタンを列ヘッダーに追加する方法について説明します。  
  
 [ドキュメント マップの作成 &#40;レポート ビルダーおよび SSRS&#41;](create-a-document-map-report-builder-and-ssrs.md)  
 サイズの大きなレポートでの移動をサポートする目次を追加する方法について説明します。  
  
 [レポートにブックマークを追加&#40;レポート ビルダーおよび SSRS&#41;](add-a-bookmark-to-a-report-report-builder-and-ssrs.md)  
 ブックマークを追加して、レポート内にリンクを作成する方法について説明します。  
  
 [URL へのハイパーリンクの追加&#40;レポート ビルダーおよび SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)  
 レポートから URL へのリンクを追加する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域&#40;レポート ビルダーおよび SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  