---
title: '[レポート データ] ペイン | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportdata.f1
- "10039"
helpviewer_keywords:
- Report Data pane
ms.assetid: aa9614a3-12e7-4e17-9de2-fafccd1f5f9d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 910f7f6d67b7e31922ed45006008d292e6f2a1c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162782"
---
# <a name="report-data-pane"></a>レポート データ ペイン
  **[レポート データ]** ペインを使用すると、レポート内で現在定義されているパラメーター、データ ソース、データセット、フィールド コレクション、および画像が表示されます。 [レポート データ] では、レポート内のデータを表すアイテムの階層ビューが表示されます。 最上位のノードは、組み込みフィールド、パラメーター、画像、およびデータ ソース参照を表します。 データ アイテムを表示するには、各ノードを展開します。 たとえば、データ ソース ノードを展開すると、そのデータ ソース用に定義されたデータセットが表示されます。 データセットを展開すると、そのフィールド コレクションが表示されます。 データをレポート ページ上のレポート アイテムにリンクするには、アイテムをレポート デザイン画面にドラッグします。  
  
## <a name="options"></a>および  
 **組み込みフィールド**  
 レポート名やページ番号など、レポートでよく使用される、Reporting Services に用意されているフィールドを表します。 詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。  
  
 **パラメーター**  
 レポート パラメーターのコレクションを表します。各パラメーターには単一の値または複数の値を指定できます。 詳細については、「[レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)」を参照してください。  
  
 **画像**  
 レポートで使用されている画像のセットを表します。 詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](../report-design/images-report-builder-and-ssrs.md)」を参照してください。  
  
 **データ ソース**  
 埋め込みデータ ソースまたは共有データ ソースへの単一のデータ ソース参照を表します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、共有データ ソースがソリューション エクスプローラーの [共有データ ソース] フォルダーの下に表示されます。 データ ソースは、Reporting Services でサポートされているデータ ソースの種類のうち 1 つを指定します。 データ ソースは、そのデータ ソースに基づくデータセットのコレクションの親ノードです。 詳細については、次を参照してください。[データ接続、データ ソース、および Reporting Services の接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)します。  
  
 **データセット**  
 1 つのデータセットを表します。 データセットは、クエリで指定され、計算フィールドを含むフィールドのコレクションの親ノードです。 Reporting Services では、クエリを指定できるようにクエリ デザイナーがサポートされています。 詳細については、次を参照してください。[レポートへのデータの追加&#40;レポート ビルダーおよび SSRS&#41; ](report-datasets-ssrs.md)と[レポート デザイナーの SQL Server Data Tools でのクエリ デザイン ツール&#40;SSRS&#41;](query-design-tools-ssrs.md)します。  
  
## <a name="see-also"></a>参照  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [グループ化ペイン](../tools/grouping-pane.md)  
  
  
