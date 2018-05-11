---
title: データベース ディメンション プロパティ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a368dd8c1179dfb5f82d004d31c2c443be775735
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="database-dimension-properties"></a>データベース ディメンション プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションの特性は、さまざまなディメンション プロパティの設定と、属性またはディメンションに含まれる階層に基づいて、ディメンションのメタデータによって定義されます。 次の表では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンション プロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**AttributeAllMemberName**|ディメンションの属性の All メンバーの名前を指定します。|  
|**[照合順序]**|ディメンションで使用する照合順序を指定します。|  
|**CurrentStorageMode**|ディメンションの現在のストレージ モードを格納します。|  
|**DependsOnDimension**|ディメンションが別のディメンションに依存している場合は、その ID を格納します。|  
|**Description**|ディメンションの説明を格納します。|  
|**ErrorConfiguration**|重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定です。|  
|**ID**|ディメンションの一意識別子 (ID) を示します。|  
|**言語**|ディメンションの既定の言語を指定します。|  
|**MdxMissingMemberMode**|欠落しているメンバーを多次元式 (MDX) ステートメントでどのように処理するかを指定します。|  
|**MiningModelID**|データ マイニング ディメンションが関連付けられているマイニング モデルの ID を保持します。 このプロパティは、ディメンションがマイニング モデル ディメンションの場合にのみ適用できます。|  
|**名前**|ディメンションの名前を指定します。|  
|**ProactiveCaching**|ディメンションのプロアクティブ キャッシュの設定を定義します。|  
|**ProcessingGroup**|処理グループを指定します。 有効値は ByAttribute または ByTable です。 既定値は**ByAttribute**です。|  
|**ProcessingMode**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によるインデックス化および集計を処理中または処理後のどちらに行うかを示します。|  
|**ProcessingPriority**|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中のディメンション処理の優先度を指定します。|  
|**ソース**|ディメンションのバインド先のデータ ソース ビューを指定します。|  
|**StorageMode**|ディメンションのストレージ モードを指定します。|  
|**型**|ディメンションの種類を指定します。|  
|**UnknownMember**|不明なメンバーが表示されるかどうかを示します。|  
|**UnknownMemberName**|ディメンションの不明なメンバーのキャプションをディメンションの既定の言語で指定します。|  
|**WriteEnabled**|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
> [!NOTE]  
>  Null 値やその他のデータ整合性の問題に取り組む際の ErrorConfiguration および UnknownMember プロパティの値を設定の詳細については、次を参照してください。 [Analysis Services 2005 でのデータの整合性問題の処理](http://go.microsoft.com/fwlink/?LinkId=81891)です。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [ディメンションのリレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [ディメンションと #40 です。Analysis Services - 多次元データ & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
