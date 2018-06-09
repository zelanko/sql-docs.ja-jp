---
title: Session 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b4c93919e6354a59aad9b42a4f6dc8373c880f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577504"
---
# <a name="session-element-xmla"></a>Session 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services のインスタンス上の既存の明示的なセッションを識別するのに、SOAP 要求メッセージの SOAP ヘッダーを使用します。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|SessionId|必要な**文字列**を使用するセッションを識別する属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はグローバル一意識別子 (GUID) を使用してセッションを識別します。|  
  
## <a name="remarks"></a>コメント  
 **セッション**ヘッダー要素で明示的に開始された既存のセッションを識別する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 **セッション**要素は、次の種類のメッセージの SOAP ヘッダーの一部。  
  
-   含む SOAP 応答、 [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) SOAP ヘッダー要素。  
  
-   実行する対象のセッションを識別する SOAP 要求、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 セッション識別子は、そのセッションが引き続き有効であることを保証するものではありません。 指定されたセッション、**セッション**要素が切れることができます。 たとえば、セッションがタイムアウトになるか、セッションに関連した接続が切断された場合には、セッションが有効期限切れになることがあります。 セッションが有効期限切れになり、有効でなくなった場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はそのセッションを終了して、現在処理中のすべてのトランザクションをロールバックします。 無効なセッション識別子を使用して送信された SOAP メッセージは失敗し、指定されたセッションが見つからないことを示す SOAP エラーが報告されます。  
  
 場合、**セッション**要素が SOAP 要求の一部として送信されない、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスの実行中のセッションを暗黙的に開始する、 **Discover**または**Execute**メソッドを呼び出すと、メソッドの呼び出しが完了したら、そのセッションを終了します。  
  
## <a name="see-also"></a>参照
 [EndSession 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [接続およびセッション管理&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
