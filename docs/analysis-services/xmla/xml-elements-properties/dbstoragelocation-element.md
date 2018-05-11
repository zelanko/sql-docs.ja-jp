---
title: DbStorageLocation 要素 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dfd4e547c6a32b5ff3d96ca7640c32567e18988c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="dbstoragelocation-element"></a>DbStorageLocation 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
  
