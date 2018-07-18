---
title: ファイルの要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb80a091c9b9585a6efc29088d15139db7033efb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970000"
---
# <a name="file-element-xmla"></a>File 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって処理するためのファイルを識別する[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)または[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンド、または親[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **ファイル**要素には、UNC ファイル名が含まれていて、親要素の使用を決定する、**ファイル**要素。  
  
 **バックアップ**コマンド、**ファイル**要素によって作成されたバックアップ ファイルの名前を指定します、**バックアップ**コマンド。 パスが指定されたパスがファイル名の一部として指定しない場合、 **BackupDir** Analysis Services のインスタンスの構成プロパティを使用します。 エラーが発生しない限り、指定したファイルが既に存在する場合、 **AllowOverwrite**要素の親の**バックアップ**に設定されているコマンド**True**します。  
  
 **復元**コマンド、**ファイル**要素によって復元されるバックアップ ファイルの名前を指定します、**復元**コマンド。  
  
 **場所**、要素、**ファイル**要素には、リモート バックアップ ファイルがについて説明します、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リモート パーティションを格納しているインスタンス。 バックアップおよびリモート パーティションを復元する詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照
 [AllowOverwrite 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
