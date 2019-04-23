---
title: ストアド プロシージャのクエリ コンテキストへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93624a612126e9103144b8b53272122e66202b8a
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156768"
---
# <a name="accessing-query-context-in-stored-procedures"></a>ストアド プロシージャのクエリ コンテキストへのアクセス
  ストアド プロシージャの実行コンテキストは、ADOMD.NET サーバー オブジェクト モデルの `Context` オブジェクトとして、ストアド プロシージャのコードで使用できます。 これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。 このオブジェクトでは次のプロパティを使用できます。  
  
|プロパティ|型|説明|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|現在のクエリ コンテキストのキューブです。|  
|**CurrentDatabaseName**|String|現在のデータベースの識別子です。|  
|**CurrentConnection**|接続|現在のコンテキストの接続オブジェクトへの参照です。|  
|**パス**|Integer|現在のコンテキストのパス番号です。|  
  
 `Context` オブジェクトは、多次元式 (MDX) オブジェクト モデルがストアド プロシージャで使用されている場合に存在し、 MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。 `Context` オブジェクトは、ストアド プロシージャに明示的に渡されたり、ストアド プロシージャから明示的に返されることはなく、 ストアド プロシージャの実行中に利用できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
