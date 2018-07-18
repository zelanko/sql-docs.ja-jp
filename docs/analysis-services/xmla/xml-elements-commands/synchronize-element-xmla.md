---
title: Synchronize 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 11804b9b6ca9ac430bdb47c0b9050b8c6995cf7f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007183"
---
# <a name="synchronize-element-xmla"></a>Synchronize 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services データベースを別の既存のデータベースと同期されます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)、[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md)、 [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **同期**コマンドはソース インスタンスとターゲット データベースを同期し、データベースで指定されて、**ソース**要素。 必要に応じて、**同期**コマンドは、ソース データベースで定義されたリモート パーティションを同期します。  
  
 バックアップのファイルに格納されているオブジェクトによって使用されるストレージ モードに応じて、**同期**コマンドは、次の表に示すように情報を同期します。  
  
|[ストレージ モード]|[情報]|  
|------------------|-----------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、**同期**コマンド、読み取りロックはソース データベースに配置され、ターゲット データベースに書き込みロックを配置します。 両方のロックが後にリリースされる、**同期**コマンドが完了しました。  
  
 データベースの同期の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照
 [バックアップ要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [要素をバッチ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [要素を並列&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Restore 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
