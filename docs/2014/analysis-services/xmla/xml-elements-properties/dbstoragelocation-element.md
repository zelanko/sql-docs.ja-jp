---
title: DbStorageLocation 要素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdee1fc2d62f63eb70e5aecd47c32693a9fbd155
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173922"
---
# <a name="dbstoragelocation-element"></a>DbStorageLocation 要素
  フォルダーを指定します、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]作成し、すべてのデータベースのデータとメタデータ ファイルを管理します。  
  
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
|データ型と長さ|String|  
|既定値|""|  
|Cardinality|0-1: 1 回だけ発生する可能性が省略可能な要素です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 `DbStorageLocation`データベース プロパティは、既存の UNC フォルダー パスまたは空の文字列に設定する必要があります。 空の文字列は、既定のサーバー データ フォルダーを示します。 フォルダーが存在しない場合、`Create` コマンド、`Attach` コマンド、または `Alter` コマンドを実行するとエラーが発生します。  
  
 さらに、`DbStorageLocation`サーバー データ フォルダーまたはそのサブフォルダーを指すデータベース プロパティを設定することはできません。 サーバー データ フォルダーまたはそのサブフォルダーを指した場合、`Create` コマンド、`Attach` コマンド、または `Alter` コマンドを実行するとエラーが発生します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Analysis Services データベースのインポートとデタッチ](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
