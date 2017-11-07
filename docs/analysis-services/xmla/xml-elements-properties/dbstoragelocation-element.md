---
title: "DbStorageLocation 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9267f5858eb837efdbcd84fb040934e767835d4f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbstoragelocation-element"></a>DbStorageLocation 要素
  フォルダーを指定場所[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を作成し、すべてのデータベース データとメタデータ ファイルを管理します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|""|  
|Cardinality|0-1: 1 回だけ発生する可能性が省略可能な要素です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[データベース](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DbStorageLocation** データベース プロパティには、既存の UNC フォルダー パスまたは空の文字列を設定する必要があります。 空の文字列は、既定のサーバー データ フォルダーを示します。 実行するときに、エラーが発生する、フォルダーが存在しない場合、**作成**、**アタッチ**、または**Alter**コマンド。  
  
 さらに、 **DbStorageLocation**サーバー データ フォルダーまたはそのサブフォルダーを指すデータベース プロパティを設定することはできません。 実行するときに、エラーが発生する場合は、サーバー データ フォルダーまたはそのサブフォルダーを指した、**作成**、**アタッチ**、または**Alter**コマンド。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [アタッチし、Analysis Services データベースのデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

