---
title: クエリのコンテキストにアクセスするストアド プロシージャ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13facbc44747bedc6f28e1ff4d3bda81b60004ad
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="accessing-query-context-in-stored-procedures"></a>ストアド プロシージャのクエリ コンテキストへのアクセス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ストアド プロシージャの実行コンテキストは、ストアド プロシージャとしてのコード内で使用可能な**コンテキスト**ADOMD.NET サーバー オブジェクト モデルのオブジェクト。 これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。 このオブジェクトでは次のプロパティを使用できます。  
  
|プロパティ|型|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|現在のクエリ コンテキストのキューブです。|  
|**CurrentDatabaseName**|文字列|現在のデータベースの識別子です。|  
|**CurrentConnection**|接続|現在のコンテキストの接続オブジェクトへの参照です。|  
|**パス**|Integer|現在のコンテキストのパス番号です。|  
  
 **コンテキスト**ストアド プロシージャで、多次元式 (MDX) オブジェクト モデルを使用すると、オブジェクトが存在します。 MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。 **コンテキスト**オブジェクトが明示的に渡されたか、ストアド プロシージャによって返されます。 ストアド プロシージャの実行中に利用できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
