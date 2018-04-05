---
title: Synchronize 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Synchronize Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords:
- Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e3361f8cdd01421561bbb6b16d4b6cf5675a356
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="synchronize-element-xmla"></a>Synchronize 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]同期、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]別の既存のデータベースとデータベースです。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)、[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md)、 [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **同期**コマンド ソース インスタンスとターゲット データベースを同期して、データベースで指定されて、**ソース**要素。 必要に応じて、**同期**コマンドは、ソース データベースで定義されたリモート パーティションを同期します。  
  
 バックアップ ファイルに格納されているオブジェクトによって使用されるストレージ モードに応じて、**同期**コマンドは、次の表に示すように情報を同期します。  
  
|[ストレージ モード]|[情報]|  
|------------------|-----------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、**同期**コマンド、読み取りロックは、ソース データベースに配置され、ターゲット データベースに書き込みロックをかけます。 両方のロックが後にリリースされた、**同期**コマンドが完了しました。  
  
 データベースの同期の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>参照  
 [Backup 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [バッチ要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Parallel 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [要素 &#40; を復元します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
