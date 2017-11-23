---
title: "Location 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Location Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords: Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 95080cae1f3740bef465197491bc7e2ce18a5915
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="location-element-xmla"></a>Location 要素 (XMLA)
  親のリモート サーバーに関する情報を含む[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
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
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|[DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)|  
|[[復元]](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)、 [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、 [%datasourcetype](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)、 [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)、 [%datasourcetype](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **バックアップ**コマンド、**場所**要素のリモート インスタンスのリモート バックアップ ファイルの作成に関する情報を提供[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 **復元**コマンド、**場所**要素を識別して、リモートへの接続に関する情報を提供[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リモート復元に使用するリモート バックアップ ファイルと同様に、インスタンスそのリモート インスタンス上のパーティションです。  
  
 **同期**コマンド、**場所**要素は、ターゲット インスタンスで使用されるデータ ソースまたは同期する必要があるソース インスタンスで定義されたリモート インスタンスのいずれかについて説明します、。値に応じて、ターゲット インスタンス、 **%datasourcetype**親要素**同期**コマンド。  
  
 バックアップと復元のリモート インスタンスの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [BackupRemotePartitions 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
