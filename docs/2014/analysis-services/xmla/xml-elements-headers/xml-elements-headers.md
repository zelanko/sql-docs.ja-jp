---
title: ヘッダー (XMLA) |Microsoft ドキュメント
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
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bb2cff2e70ccd1ac0cf391f7832db4978a415f56
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174336"
---
# <a name="headers-xmla"></a>ヘッダー (XMLA)
  XML for Analysis (XMLA) プロトコルでは、セッション サポートやサポートされる機能のネゴシエーションなど、プロトコルレベルの機能を管理するために、SOAP ヘッダー内で XML 要素を使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、によって実装される XMLA ヘッダー要素[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
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
  
  