---
title: XML for Analysis (XMLA) リファレンス |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e8c3645175d8d1f3251fd621825f5a542669cbb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576764"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) リファレンス
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]   

Azure の Analysis Services と SQL Server Analysis Services は、クライアント アプリケーションと Analysis Services インスタンス間の通信 Analysis (XMLA) プロトコルの XML を使用します。 最も基本的なレベルでは、XMLA だけを使用する Analysis Services インスタンスとの仲介役として、ADOMD.NET や AMO などの他のクライアント ライブラリが要求の作成と応答のデコードを XMLA で行います。  
  
 テーブルと多次元の両方のモードの検出とデータの操作をサポートするために XMLA 仕様は 2 つの一般的にアクセス可能なメソッドを定義[Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)と[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)、およびXML 要素とデータ型のコレクションです。 XML は疎結合のクライアント/サーバー アーキテクチャを可能にするため、2 つのメソッドは送受信される情報を XML 形式で処理します。 

Analysis Services は XMLA 1.1  仕様ではなくに注釈として実装されるデータ定義と操作の機能を追加するため、 **Discover**と**Execute**メソッドです。 拡張 XML 構文は、表形式モデル スクリプト言語 (TMSL) および Analysis Services スクリプト言語 (ASSL) です。 

TMSL は、表形式モデルのデータベース互換性レベル 1200 以降のコマンドとオブジェクト モデル定義構文です。 TMSL は、XMLA プロトコルを使って、Analysis Services と通信する場所、`XMLA.Execute`メソッドは TMSL で JSON ベースのステートメントのスクリプトおよび Analysis Services スクリプト言語 (ASSL を XMLA) で従来 XML ベースのスクリプトを受け取ります。 詳細については、次を参照してください。 [Tabular Model Scripting Language (TMSL) 参照](../tabular-model-scripting-language-tmsl-reference.md)です。

ASSL は、多次元モデル データベースと表形式モードのデータベース互換性レベル 1103 以下のコマンドとオブジェクト モデルの定義構文です。 この定義は、互換性に影響することがなく、XMLA 仕様に基づいています。 XMLA だけを使用するか、XMLA と ASSL を一緒に使用するかに関係なく、XMLA に基づく相互運用性は確保されます。 詳細については、次を参照してください。 [Analysis Services スクリプト言語 (ASSL を XMLA)](../scripting/analysis-services-scripting-language-assl-for-xmla.md)です。
  
 開発者は、ソリューションの要件は、XML、SOAP、HTTP などの標準のプロトコルを指定する場合に、インターフェイスとして XMLA を使用できます。 開発者および管理者できますも XMLA を使用してアドホックごとに、サーバーから情報を取得またはコマンドを実行します。 
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XML データ型 (XMLA)](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|XMLA 仕様のデータ型について説明します。|  
|[XML 要素のコマンド (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Execute メソッドの呼び出し中に、コマンド要素内で使用できる要素です。|  
|[XML 要素のコマンド (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Execute メソッドの呼び出し中に、コマンド要素内で使用できる要素です。|  
|[XML 要素のヘッダー (XMLA)](../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)| Microsoft Analysis Services によって実装されるヘッダー要素です。|  
|[XML 要素のプロパティ (XMLA)](../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)| プロパティの情報と XMLA ヘッダー、メソッド、オブジェクト、コマンド、およびデータ型の値を表す要素。|  
|[メソッドで-の XML 要素 (XMLA) の検出します。](../../analysis-services/xmla/xml-elements-methods-discover.md)| Analysis Services のインスタンスから使用可能なデータベースまたは特定のオブジェクトに関する詳細情報の一覧などの情報を取得します。|  
|[XML 要素のメソッドの実行 (XMLA)](../../analysis-services/xmla/xml-elements-methods-execute.md)| For Analysis (XMLA) コマンドの XML を Analysis Services のインスタンスに送信します。|  
|[XML 要素のオブジェクトの DiscoverResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)| Discover メソッド呼び出しへの応答には、Analysis Services のインスタンスによって返される情報が含まれています。|  
|[XML 要素のオブジェクトの ExecuteResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)| Execute メソッド呼び出しへの応答には、Analysis Services のインスタンスによって返される情報が含まれています。|  
|[XML 要素のオブジェクト (XMLA)](../../analysis-services/xmla/xml-elements-objects.md)| Analysis Services によって実装されているオブジェクト。|  
|[XML for Analysis への準拠 (XMLA)](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|XMLA 1.1 仕様への準拠のレベルについて説明します。|  
  
## <a name="see-also"></a>参照
 [XML for Analysis Schema 行セット](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
 [ADOMD.NET での開発](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 [分析管理オブジェクト &#40;AMO&#41; による開発](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
