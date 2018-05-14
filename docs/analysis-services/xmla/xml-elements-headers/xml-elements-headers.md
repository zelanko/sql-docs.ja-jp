---
title: ヘッダー (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 17f859d5bf8950508cb744c39fb69366b9df24a3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---headers"></a>ヘッダーの XML 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  XML for Analysis (XMLA) プロトコルでは、セッション サポートやサポートされる機能のネゴシエーションなど、プロトコルレベルの機能を管理するために、SOAP ヘッダー内で XML 要素を使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、によって実装される XMLA ヘッダー要素[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
|方法|説明|  
|------------|-----------------|  
|[BeginSession 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンス上で新しいセッションを開始するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[EndSession 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の既存のセッションを終了するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[Session 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の既存の明示的なセッションを識別するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[ProtocolCapabilities 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとクライアント アプリケーションの間のプロトコル機能を識別するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
  
## <a name="see-also"></a>参照  
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML データ型 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
