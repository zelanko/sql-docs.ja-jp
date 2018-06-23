---
title: DbStorageLocation 要素 |Microsoft ドキュメント
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
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 651dc0424c492efefa7828ae327f9bdcf837ed77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083046"
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
|データ型と長さ|String|  
|既定値|""|  
|Cardinality|0-1: 1 回だけ発生する可能性が省略可能な要素です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DbStorageLocation`データベース プロパティは、既存の UNC フォルダー パスまたは空の文字列に設定する必要があります。 空の文字列は、既定のサーバー データ フォルダーを示します。 フォルダーが存在しない場合、`Create` コマンド、`Attach` コマンド、または `Alter` コマンドを実行するとエラーが発生します。  
  
 さらに、`DbStorageLocation`サーバー データ フォルダーまたはそのサブフォルダーを指すデータベース プロパティを設定することはできません。 サーバー データ フォルダーまたはそのサブフォルダーを指した場合、`Create` コマンド、`Attach` コマンド、または `Alter` コマンドを実行するとエラーが発生します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Analysis Services データベースのインポートとデタッチ](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  