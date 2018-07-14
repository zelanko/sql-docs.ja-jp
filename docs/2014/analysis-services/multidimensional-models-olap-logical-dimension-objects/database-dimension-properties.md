---
title: データベース ディメンション プロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e9b86509f0b4a5ab87102c43838cfa1b18376a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194332"
---
# <a name="database-dimension-properties"></a>データベース ディメンション プロパティ
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションの特性は、さまざまなディメンション プロパティの設定と、属性またはディメンションに含まれる階層に基づいて、ディメンションのメタデータによって定義されます。 次の表では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンション プロパティについて説明します。  
  
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
|`ProcessingGroup`|処理グループを指定します。 有効値は ByAttribute または ByTable です。 既定値は`ByAttribute`します。|  
|`ProcessingMode`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるインデックス化および集計を処理中または処理後のどちらに行うかを示します。|  
|`ProcessingPriority`|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中のディメンション処理の優先度を指定します。|  
|`Source`|ディメンションのバインド先のデータ ソース ビューを指定します。|  
|`StorageMode`|ディメンションのストレージ モードを指定します。|  
|`Type`|ディメンションの種類を指定します。|  
|`UnknownMember`|不明なメンバーが表示されるかどうかを示します。|  
|`UnknownMemberName`|ディメンションの不明なメンバーのキャプションをディメンションの既定の言語で指定します。|  
|`WriteEnabled`|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
> [!NOTE]  
>  Null 値やその他のデータ整合性の問題を使用する場合の ErrorConfiguration および UnknownMember プロパティの値を設定する方法についての詳細については、次を参照してください。 [Analysis Services 2005 でのデータの整合性問題の処理](http://go.microsoft.com/fwlink/?LinkId=81891)します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](attributes-and-attribute-hierarchies.md)   
 [ユーザー階層](user-hierarchies.md)   
 [ディメンションのリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [ディメンション&#40;Analysis Services - 多次元データ&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
