---
title: ヘッダー (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc6c9ebfef18b108c31870c5703cac3841cfc29
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155700"
---
# <a name="headers-xmla"></a>ヘッダー (XMLA)
  XML for Analysis (XMLA) プロトコルでは、セッション サポートやサポートされる機能のネゴシエーションなど、プロトコルレベルの機能を管理するために、SOAP ヘッダー内で XML 要素を使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、XMLA ヘッダー要素によって実装される[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
|方法|説明|  
|------------|-----------------|  
|[BeginSession 要素&#40;XMLA&#41;](session-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンス上で新しいセッションを開始するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[EndSession 要素&#40;XMLA&#41;](endsession-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の既存のセッションを終了するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[Session 要素&#40;XMLA&#41;](session-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の既存の明示的なセッションを識別するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
|[ProtocolCapabilities 要素&#40;XMLA&#41;](protocolcapabilities-element-xmla.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとクライアント アプリケーションの間のプロトコル機能を識別するために、SOAP 要求メッセージ内で SOAP ヘッダーを使用します。|  
  
## <a name="see-also"></a>参照  
 [XML 要素&#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML データ型&#40;XMLA&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [XML 要素&#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  
