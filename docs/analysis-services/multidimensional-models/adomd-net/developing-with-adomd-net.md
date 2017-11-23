---
title: "ADOMD.NET での開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords: ADOMD.NET
ms.assetid: abaf33aa-db55-43bf-8f30-15547559be1d
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 445f0aaef60f44f7dcf7f1b08676fa4c0956a65d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="developing-with-adomdnet"></a>ADOMD.NET での開発
  ADOMD.NET は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework データ プロバイダーと通信するように設計された[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 ADOMD.NET は、XML for Analysis プロトコルを使用して分析データ ソースとやり取りします。その際、TCP/IP 接続または HTTP 接続を使用して、XML for Analysis 仕様準拠の SOAP 要求と応答を送受信します。 コマンドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、Analysis Services スクリプト言語 (ASSL)、または SQL の一部の構文で送ることができ、結果を返さない場合があります。 分析データ、主要業績評価指標 (KPI)、マイニング モデルは、ADOMD.NET オブジェクト モデルを使用することによって、取得と操作を行うことができます。 ADOMD.NET を使用すると、OLE DB 準拠のスキーマ行セットを取得するか、ADOMD.NET オブジェクト モデルを使用することによって、メタデータを表示および操作することもできます。  
  
 ADOMD.NET データ プロバイダーがによって表される、 **Microsoft.AnalysisServices.AdomdClient**名前空間。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[ADOMD.NET クライアント プログラミング](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|ADOMD.NET クライアント オブジェクトを使用して、分析データ ソースからデータおよびメタデータを取得する方法について説明します。|  
|[ADOMD.NET サーバー プログラミング](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|ADOMD.NET サーバー オブジェクトを使用して、ストアド プロシージャおよびユーザー定義関数を作成する方法について説明します。|  
|[ADOMD.NET の再配布](../../../analysis-services/multidimensional-models/adomd-net/redistributing-adomd-net.md)|ADOMD.NET の再配布プロセスについて説明します。|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|含まれているオブジェクトの詳細、 **Microsoft.AnalysisServices.AdomdClient**名前空間。|  
  
## <a name="see-also"></a>参照  
 [多次元式 &#40;です。MDX と #41 です。参照](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../../../dmx/data-mining-extensions-dmx-reference.md)   
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Analysis Services スクリプト言語 &#40; を使用した開発ASSL &#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [多次元モデルのデータ アクセスと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
