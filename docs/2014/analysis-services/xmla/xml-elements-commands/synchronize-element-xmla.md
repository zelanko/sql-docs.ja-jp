---
title: Synchronize 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Synchronize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords:
- Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f88b07721d391c1f834ed93d21039753728081d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187099"
---
# <a name="synchronize-element-xmla"></a>Synchronize 要素 (XMLA)
  同期、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を別の既存のデータベースのデータベース。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md)、[場所](../xml-elements-properties/locations-element-xmla.md)、[ソース](../xml-elements-properties/source-element-synchronize-xmla.md)、 [SynchronizeSecurity](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Synchronize` コマンドは、同期先データベースを、`Source` 要素で指定された同期元インスタンスおよびデータベースと同期させます。 さらに、`Synchronize` コマンドは同期元データベース上に定義されたリモート パーティションを同期させることもできます。  
  
 `Synchronize` コマンドは、バックアップ ファイルに保存されたオブジェクトのストレージ モードに応じて、次の表のように情報を同期します。  
  
|[ストレージ モード]|[情報]|  
|------------------|-----------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 `Synchronize` コマンドの実行中に、同期元データベースに読み取りロックが設定され、同期先データベースに書き込みロックが設定されます。 `Synchronize` コマンドが完了した後、両者のロックは解放されます。  
  
 データベースの同期の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [バックアップ要素&#40;XMLA&#41;](backup-element-xmla.md)   
 [要素をバッチ&#40;XMLA&#41;](batch-element-xmla.md)   
 [要素を並列&#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Restore 要素&#40;XMLA&#41;](restore-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
