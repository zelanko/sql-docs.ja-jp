---
title: ファイルの要素 (XMLA) |Microsoft ドキュメント
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
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575194"
---
# <a name="file-element-xmla"></a>File 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親で使用するファイルを識別[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)または[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンド、または親[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)要素。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **ファイル**要素には、UNC ファイル名が含まれています。 および親要素の使用を決定する、**ファイル**要素。  
  
 **バックアップ**コマンド、**ファイル**要素によって作成されたバックアップ ファイルの名前を決定する、**バックアップ**コマンド。 パスがで指定されたパスがファイル名の一部として指定しない場合、 **BackupDir** Analysis Services のインスタンスの構成プロパティを使用します。 しない限り、エラーが発生した、指定したファイルが既に存在する場合、 **AllowOverwrite**の親要素**バックアップ**コマンドに設定されている**True**です。  
  
 **復元**コマンド、**ファイル**要素を決定することで復元するバックアップ ファイルの名前、**復元**コマンド。  
  
 **場所**、要素、**ファイル**要素の場合は、リモート バックアップ ファイルに記述、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リモート パーティションが含まれているインスタンス。 バックアップと、リモート パーティションの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照
 [AllowOverwrite 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
