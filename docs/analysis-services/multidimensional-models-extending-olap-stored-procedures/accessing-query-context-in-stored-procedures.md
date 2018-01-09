---
title: "クエリのコンテキストにアクセスするストアド プロシージャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5b7a0c3e57a5249a26bf13a2cf9709e58df85da8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="accessing-query-context-in-stored-procedures"></a>ストアド プロシージャのクエリ コンテキストへのアクセス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ストアド プロシージャの実行コンテキストは、ストアド プロシージャとしてのコード内で使用可能な**コンテキスト**ADOMD.NET サーバー オブジェクト モデルのオブジェクト。 これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。 このオブジェクトでは次のプロパティを使用できます。  
  
|プロパティ|型|Description|  
|--------------|----------|-----------------|  
|**[Currentcube]**|Cube|現在のクエリ コンテキストのキューブです。|  
|**CurrentDatabaseName**|String|現在のデータベースの識別子です。|  
|**CurrentConnection**|接続|現在のコンテキストの接続オブジェクトへの参照です。|  
|**パス**|Integer|現在のコンテキストのパス番号です。|  
  
 **コンテキスト**ストアド プロシージャで、多次元式 (MDX) オブジェクト モデルを使用すると、オブジェクトが存在します。 MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。 **コンテキスト**オブジェクトが明示的に渡されたか、ストアド プロシージャによって返されます。 ストアド プロシージャの実行中に利用できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
