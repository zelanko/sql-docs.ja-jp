---
title: XML for Analysis (XMLA) リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec0d843ac46cbcf5d032d1f93190869fd5a37cb2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241282"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) リファレンス
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XML for Analysis (XMLA) プロトコルを使用して、クライアント アプリケーションと Analysis Services インスタンスの間のすべての通信を処理します。 最も基本的なレベルでは、XMLA だけを使用する Analysis Services インスタンスとの仲介役として、ADOMD.NET や AMO などの他のクライアント ライブラリが要求の作成と応答のデコードを XMLA で行います。  
  
 多次元と表形式の両方の形式の検出とデータの操作をサポートするために、XMLA 仕様は 2 つの一般的にアクセス可能なメソッドを定義します[Discover](xml-elements-methods-discover.md)と[Execute](xml-elements-methods-execute.md)、およびXML 要素とデータ型のコレクションです。 XML は疎結合のクライアント/サーバー アーキテクチャを可能にするため、2 つのメソッドは送受信される情報を XML 形式で処理します。 Analysis Services は XMLA 1.1  仕様に準拠していますが、拡張してデータの定義と操作の機能を追加することもできます。これは、`Discover` メソッドと `Execute` メソッドで注釈として実装されます。 拡張 XML 構文は、Analysis Services スクリプト言語 (ASSL) と呼ばれます。 ASSL は、完全に XMLA 仕様をベースに作成されています。 XMLA だけを使用するか、XMLA と ASSL を一緒に使用するかに関係なく、XMLA に基づく相互運用性は確保されます。  
  
 ソリューションの要件で XML、SOAP、HTTP などの標準的なプロトコルが指定されている場合、プログラマは XMLA をプログラム インターフェイスとして使用できます。 プログラマと管理者は、適宜 XMLA を使用して、サーバーから情報を取得したり、コマンドを実行したりすることもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XML 要素&#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)|XMLA 仕様の要素について説明します。|  
|[XML データ型&#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)|XMLA 仕様のデータ型について説明します。|  
|[XML for Analysis への準拠&#40;XMLA&#41;](xml-for-analysis-compliance-xmla.md)|XMLA 1.1 仕様への準拠のレベルについて説明します。|  
  
## <a name="related-sections"></a>関連項目  
 [Services スクリプト言語の分析を使用した開発&#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis Schema 行セット](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [ADOMD.NET での開発](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [分析管理オブジェクトを使用した開発&#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft OLAP アーキテクチャについて](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
