---
title: Location 要素 (XMLA) |Microsoft ドキュメント
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
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 51b0838b9843658b4081f9464c63274631ed74be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176695"
---
# <a name="location-element-xmla"></a>Location 要素 (XMLA)
  親のリモート サーバーに関する情報を含む[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
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
 `Backup`コマンド、`Location`要素のリモート インスタンスのリモート バックアップ ファイルの作成に関する情報を提供[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 `Restore` コマンドの場合、`Location` 要素は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のリモート インスタンスを識別して接続するための情報、およびそのリモート インスタンス上のリモート パーティションの復元に使用されるリモート バックアップ ファイルについての情報を提供します。  
  
 `Synchronize` コマンドの場合、`Location` 要素は、親コマンド `DataSourceType` の `Synchronize` 要素の値に応じて、同期先インスタンスによって使用されるデータ ソース、あるいは同期先インスタンスと同期される同期元インスタンス上に定義されたリモート インスタンスを示します。  
  
 バックアップと復元のリモート インスタンスの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [BackupRemotePartitions 要素&#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  