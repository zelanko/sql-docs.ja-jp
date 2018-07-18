---
title: BackupRemotePartitions 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33e81bd76e7f900a396b1f9bfbae808092a2877e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007115"
---
# <a name="backupremotepartitions-element-xmla"></a>BackupRemotePartitions 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  決定かどうか、親[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)コマンドは、オブジェクトに関連付けられているリモート パーティションをバックアップします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup>  
   ...  
   <BackupRemotePartitions>...</BackupRemotePartitions>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 場合**BackupRemotePartitions**に設定されている**True**、**場所**要素を 1 つまたは複数を含む**場所**要素を含める必要があります。**バックアップ**コマンド、またはエラーが発生します。 バックアップおよびリモート パーティションを復元する詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照
 [Locations 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)   
 [Location 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
