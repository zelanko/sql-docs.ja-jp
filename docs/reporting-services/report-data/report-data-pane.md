---
title: '[レポート データ] ペイン | Microsoft Docs'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
f1_keywords:
- "10039"
- sql13.rtp.rptdesigner.reportdata.f1
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: aa9614a3-12e7-4e17-9de2-fafccd1f5f9d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03fb902cc4150ef9ab0eed9774a3c67fe427de6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611529"
---
# <a name="report-data-pane"></a>レポート データ ペイン
  **[レポート データ]** ペインを使用すると、レポート内で現在定義されているパラメーター、データ ソース、データセット、フィールド コレクション、および画像が表示されます。 [レポート データ] ペインでは、レポート内のデータを表すアイテムの階層ビューが表示されます。 最上位のノードは、組み込みフィールド、パラメーター、画像、およびデータ ソース参照を表します。 データ アイテムを表示するには、各ノードを展開します。 たとえば、データ ソース ノードを展開すると、そのデータ ソース用に定義されたデータセットが表示されます。 データセットを展開すると、そのフィールド コレクションが表示されます。 データをレポート ページ上のレポート アイテムにリンクするには、アイテムをレポート デザイン画面にドラッグします。  
  
## <a name="options"></a>[変数]  
 **組み込みフィールド**  
 レポート名やページ番号など、レポートでよく使用される、Reporting Services に用意されているフィールドを表します。 詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。  
  
 **パラメーター**  
 レポート パラメーターのコレクションを表します。各パラメーターには単一の値または複数の値を指定できます。 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)にあります。  
  
 **画像**  
 レポートで使用されている画像のセットを表します。 詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)」を参照してください。  
  
 **データ ソース**  
 埋め込みデータ ソースまたは共有データ ソースへの単一のデータ ソース参照を表します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、共有データ ソースがソリューション エクスプローラーの [共有データ ソース] フォルダーの下に表示されます。 データ ソースは、Reporting Services でサポートされているデータ ソースの種類のうち 1 つを指定します。 データ ソースは、そのデータ ソースに基づくデータセットのコレクションの親ノードです。 詳細については、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」を参照してください。  
  
 **データセット**  
 1 つのデータセットを表します。 データセットは、クエリで指定され、計算フィールドを含むフィールドのコレクションの親ノードです。 Reporting Services では、クエリを指定できるようにクエリ デザイナーがサポートされています。 詳細については、「[レポート データセット &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)」および「[クエリ デザイン ツール &#40;SSRS&#41;](../../reporting-services/report-data/query-design-tools-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [グループ化ペイン](../../reporting-services/tools/grouping-pane.md)  
  
  
