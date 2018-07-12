---
title: ADOMD.NET での開発 |Microsoft Docs
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
- ADOMD.NET
ms.assetid: abaf33aa-db55-43bf-8f30-15547559be1d
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ff460d496b1ef148b5da7e0dbada2835fb1328c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151853"
---
# <a name="developing-with-adomdnet"></a>ADOMD.NET での開発
  ADOMD.NET は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework データ プロバイダーと通信するように設計された[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 ADOMD.NET は、XML for Analysis プロトコルを使用して分析データ ソースとやり取りします。その際、TCP/IP 接続または HTTP 接続を使用して、XML for Analysis 仕様準拠の SOAP 要求と応答を送受信します。 コマンドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、Analysis Services スクリプト言語 (ASSL)、または SQL の一部の構文で送ることができ、結果を返さない場合があります。 分析データ、主要業績評価指標 (KPI)、マイニング モデルは、ADOMD.NET オブジェクト モデルを使用することによって、取得と操作を行うことができます。 ADOMD.NET を使用すると、OLE DB 準拠のスキーマ行セットを取得するか、ADOMD.NET オブジェクト モデルを使用することによって、メタデータを表示および操作することもできます。  
  
 ADOMD.NET データ プロバイダーがによって表される、`Microsoft.AnalysisServices.AdomdClient`名前空間。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[ADOMD.NET クライアント プログラミング](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|ADOMD.NET クライアント オブジェクトを使用して、分析データ ソースからデータおよびメタデータを取得する方法について説明します。|  
|[ADOMD.NET サーバー プログラミング](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|ADOMD.NET サーバー オブジェクトを使用して、ストアド プロシージャおよびユーザー定義関数を作成する方法について説明します。|  
|[ADOMD.NET の再配布](redistributing-adomd-net.md)|ADOMD.NET の再配布プロセスについて説明します。|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|`Microsoft.AnalysisServices.AdomdClient` 名前空間に含まれているオブジェクトの詳細を説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元式&#40;MDX&#41;リファレンス](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [データ マイニング拡張機能&#40;DMX&#41;リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [Services スクリプト言語の分析を使用した開発&#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [多次元モデルのデータ アクセス&#40;Analysis Services - 多次元データ&#41;](../mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
