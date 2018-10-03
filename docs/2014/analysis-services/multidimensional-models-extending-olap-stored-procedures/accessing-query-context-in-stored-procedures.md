---
title: ストアド プロシージャのクエリ コンテキストへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: f6c5a22a6bc3768e324ca45805ff510b1a86668c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142222"
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
  
  
