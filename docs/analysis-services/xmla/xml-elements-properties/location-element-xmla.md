---
title: Location 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4953981e7657706a986e9a2407f6786ff676a854
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38004494"
---
# <a name="location-element-xmla"></a>Location 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親のリモート サーバーに関する情報を格納[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <Location>  
```  
  
```  
  
<File>...</File> <!-- for Backup and Restore only -->  
<DataSourceID>...</DataSourceID>  
<DataSourceType>...</DataSourceType> <!-- for Restore and Synchronize only -->  
<ConnectionString>...</ConnectionString> <!-- for Restore and Synchronize only -->  
<Folders>...</Folders> <!-- for Restore and Synchronize only -->  
```  
  
```  
  
   </Location>  
   ...  
</Backup>  
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
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[[復元]](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)、 [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、 [%datasourcetype](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)、 [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、 [%datasourcetype](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **バックアップ**コマンド、**場所**要素は、Analysis Services のリモート インスタンスのリモート バックアップ ファイルの作成についての情報を提供します。  
  
 **復元**コマンド、**場所**要素が識別し、リモート接続に関する情報を提供[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リモートを復元するために使用するリモート バックアップ ファイルと同様に、インスタンスそのリモート インスタンス上のパーティション。  
  
 **同期**コマンド、**場所**要素は、ターゲット インスタンスで使用されるデータ ソースまたはソース インスタンスと同期する必要がありますで定義されたリモート インスタンスのいずれかについて説明します、。ターゲット インスタンスの値に応じて、 **%datasourcetype**親要素**同期**コマンド。  
  
 バックアップと復元のリモート インスタンスの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照
 [BackupRemotePartitions 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
