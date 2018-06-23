---
title: 変数とパラメーター (MDX) の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a2e477c1faa1f8bed7568c510418abb006875f48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075136"
---
# <a name="using-variables-and-parameters-mdx"></a>変数とパラメーターの使用 (MDX)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]では、多次元式 (MDX) ステートメントをパラメーター化できます。 ステートメントをパラメーター化すれば、実行時にカスタマイズ可能な汎用ステートメントを作成できます。  
  
 パラメーター化されたステートメントを作成するときには、パラメーター名の前に @ 記号を付けることによってパラメーター名を識別します。 たとえば、@Year有効なパラメーター名になります  
  
 MDX は、リテラルまたはスカラー値用のパラメーターだけをサポートします。 メンバー、セット、または組を参照するパラメーターを作成するには、 [StrToMember](/sql/mdx/strtomember-mdx) や [StrToSet](/sql/mdx/strtoset-mdx)などの関数を使う必要があります。  
  
 次の XML for Analysis (XMLA) の例で、@CountryNameパラメーターには、データが取得される顧客の国にが含まれます。  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 この機能を OLE DB を使用するには、使用、`ICommandWithParameters`インターフェイスです。 ADOMD.Net でこの機能を使用するには、 **AdomdCommand.Parameters** コレクションを使用します。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプティングの基礎&#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
