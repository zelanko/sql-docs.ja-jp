---
title: XML for Analysis (XMLA) リファレンス |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 514e886357fe388a344b7b434bf7042bab5375e7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) リファレンス
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クライアント アプリケーションと Analysis Services インスタンスの間のすべての通信を処理するのにには、XML for Analysis (XMLA) プロトコルを使用します。 最も基本的なレベルでは、XMLA だけを使用する Analysis Services インスタンスとの仲介役として、ADOMD.NET や AMO などの他のクライアント ライブラリが要求の作成と応答のデコードを XMLA で行います。  
  
 多次元と表形式の両方の形式で検出とデータの操作をサポートするために XMLA 仕様は 2 つの一般的にアクセス可能なメソッドを定義[Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)と[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)、およびXML 要素とデータ型のコレクションです。 XML は疎結合のクライアント/サーバー アーキテクチャを可能にするため、2 つのメソッドは送受信される情報を XML 形式で処理します。 Analysis Services は XMLA 1.1  仕様ではなくに注釈として実装されるデータ定義と操作の機能を追加するため、 **Discover**と**Execute**メソッドです。 拡張 XML 構文は、Analysis Services スクリプト言語 (ASSL) と呼ばれます。 ASSL は、完全に XMLA 仕様をベースに作成されています。 XMLA だけを使用するか、XMLA と ASSL を一緒に使用するかに関係なく、XMLA に基づく相互運用性は確保されます。  
  
 ソリューションの要件で XML、SOAP、HTTP などの標準的なプロトコルが指定されている場合、プログラマは XMLA をプログラム インターフェイスとして使用できます。 プログラマと管理者は、適宜 XMLA を使用して、サーバーから情報を取得したり、コマンドを実行したりすることもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|XMLA 仕様の要素について説明します。|  
|[XML データ型&#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|XMLA 仕様のデータ型について説明します。|  
|[XML for Analysis への準拠&#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|XMLA 1.1 仕様への準拠のレベルについて説明します。|  
  
## <a name="related-sections"></a>関連項目  
 [Analysis Services スクリプト言語 & #40; を使用した開発ASSL & #41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis スキーマ行セット](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [ADOMD.NET での開発](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [分析管理オブジェクト & #40; を使用した開発AMO & #41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft OLAP アーキテクチャについて](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
