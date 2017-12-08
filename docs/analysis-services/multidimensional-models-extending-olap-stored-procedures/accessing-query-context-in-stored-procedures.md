---
title: "クエリのコンテキストにアクセスするストアド プロシージャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: d2a53ac7fb66ded14a7e79dee881755fc7ecd45e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="accessing-query-context-in-stored-procedures"></a>ストアド プロシージャのクエリ コンテキストへのアクセス
  ストアド プロシージャの実行コンテキストは、ストアド プロシージャとしてのコード内で使用可能な**コンテキスト**ADOMD.NET サーバー オブジェクト モデルのオブジェクト。 これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。 このオブジェクトでは次のプロパティを使用できます。  
  
|プロパティ|[種類]|Description|  
|--------------|----------|-----------------|  
|**[Currentcube]**|Cube|現在のクエリ コンテキストのキューブです。|  
|**CurrentDatabaseName**|文字列|現在のデータベースの識別子です。|  
|**CurrentConnection**|接続|現在のコンテキストの接続オブジェクトへの参照です。|  
|**パス**|Integer|現在のコンテキストのパス番号です。|  
  
 **コンテキスト**ストアド プロシージャで、多次元式 (MDX) オブジェクト モデルを使用すると、オブジェクトが存在します。 MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。 **コンテキスト**オブジェクトが明示的に渡されたか、ストアド プロシージャによって返されます。 ストアド プロシージャの実行中に利用できます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
