---
title: Location 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Location Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0277ab50eb7390d3272c309df8dc865ff088c89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107614"
---
# <a name="location-element-xmla"></a>Location 要素 (XMLA)
  親のリモート サーバーに関する情報を格納[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、[同期](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>子要素  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[バックアップ](id-element-xmla.md)、[ファイル](file-element-xmla.md)|  
|[復元](connectionstring-element-xmla.md)、 [DataSourceID](datasourceid-element-xmla.md)、 [%datasourcetype](type-element-xmla.md)、[ファイル](file-element-xmla.md)、[フォルダー](folders-element-xmla.md)|  
|[同期](../xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](connectionstring-element-xmla.md)、 [DataSourceID](datasourceid-element-xmla.md)、 [%datasourcetype](type-element-xmla.md)、[フォルダー](folders-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Backup`コマンド、`Location`要素は、のリモート インスタンスの場合は、リモート バックアップ ファイルの作成についての情報を提供します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 `Restore` コマンドの場合、`Location` 要素は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のリモート インスタンスを識別して接続するための情報、およびそのリモート インスタンス上のリモート パーティションの復元に使用されるリモート バックアップ ファイルについての情報を提供します。  
  
 `Synchronize` コマンドの場合、`Location` 要素は、親コマンド `DataSourceType` の `Synchronize` 要素の値に応じて、同期先インスタンスによって使用されるデータ ソース、あるいは同期先インスタンスと同期される同期元インスタンス上に定義されたリモート インスタンスを示します。  
  
 バックアップと復元のリモート インスタンスの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [BackupRemotePartitions 要素&#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
