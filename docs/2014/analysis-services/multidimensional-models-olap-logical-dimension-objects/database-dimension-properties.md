---
title: データベースディメンションのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545192"
---
# <a name="database-dimension-properties"></a>データベース ディメンション プロパティ
  で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ディメンションの特性は、さまざまなディメンションプロパティの設定およびディメンションに含まれる属性または階層に基づいて、ディメンションのメタデータによって定義されます。 次の表では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンション プロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`AttributeAllMemberName`|ディメンションの属性の All メンバーの名前を指定します。|  
|`Collation`|ディメンションで使用する照合順序を指定します。|  
|`CurrentStorageMode`|ディメンションの現在のストレージ モードを格納します。|  
|`DependsOnDimension`|ディメンションが別のディメンションに依存している場合は、その ID を格納します。|  
|`Description`|ディメンションの説明を格納します。|  
|`ErrorConfiguration`|重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定です。|  
|`ID`|ディメンションの一意識別子 (ID) を示します。|  
|`Language`|ディメンションの既定の言語を指定します。|  
|`MdxMissingMemberMode`|欠落しているメンバーを多次元式 (MDX) ステートメントでどのように処理するかを指定します。|  
|`MiningModelID`|データ マイニング ディメンションが関連付けられているマイニング モデルの ID を保持します。 このプロパティは、ディメンションがマイニング モデル ディメンションの場合にのみ適用できます。|  
|`Name`|ディメンションの名前を指定します。|  
|`ProactiveCaching`|ディメンションのプロアクティブ キャッシュの設定を定義します。|  
|`ProcessingGroup`|処理グループを指定します。 有効値は ByAttribute または ByTable です。 既定値は `ByAttribute` です。|  
|`ProcessingMode`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるインデックス化および集計を処理中または処理後のどちらに行うかを示します。|  
|`ProcessingPriority`|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中のディメンション処理の優先度を指定します。|  
|`Source`|ディメンションのバインド先のデータ ソース ビューを指定します。|  
|`StorageMode`|ディメンションのストレージ モードを指定します。|  
|`Type`|ディメンションの種類を指定します。|  
|`UnknownMember`|不明なメンバーが表示されるかどうかを示します。|  
|`UnknownMemberName`|ディメンションの不明なメンバーのキャプションをディメンションの既定の言語で指定します。|  
|`WriteEnabled`|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
> [!NOTE]  
>  Null 値やその他のデータの整合性の問題を処理するときの ErrorConfiguration プロパティと UnknownMember プロパティの値の設定の詳細については、「 [Analysis Services 2005 でのデータ整合性の問題の処理](https://go.microsoft.com/fwlink/?LinkId=81891)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](attributes-and-attribute-hierarchies.md)   
 [ユーザー階層](user-hierarchies.md)   
 [ディメンションのリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [ディメンション &#40;Analysis Services - 多次元データ&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
