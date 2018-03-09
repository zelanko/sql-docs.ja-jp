---
title: "Cancel 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Cancel Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords: Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c50ff4e923e046a157c06ccb139e1b8645d1e9aa
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cancel-element-xmla"></a>Cancel 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]現在実行中のコマンドを取り消します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Cancel>  
      <ConnectionID>...</ConnectionID>  
      <SessionID>...</SessionID>  
      <SPID>...</SPID>  
      <CancelAssociated>...</CancelAssociated>  
   </Cancel>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[CancelAssociated](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)、 [ConnectionID](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)、 [SessionID](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)、 [SPID](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **キャンセル**コマンドを取り消しますが現在のセッションのコンテキスト内のコマンドを実行します。 クライアント アプリケーションがセッションをまだ要求していない場合は、コマンドをキャンセルできません。  
  
 場合、**キャンセル**の実行中にコマンドが実行される、**バッチ**コマンド、全体**バッチ**コマンドが取り消されました。 場合、**バッチ**コマンドがトランザクション、すべてのコマンドに含まれる、**バッチ**コマンドをロールバックします。 場合、**バッチ**コマンドがトランザクション型でないに含まれるコマンドのみ、**バッチ**時に実行されたコマンド、**キャンセル**コマンドの実行は、ロールバックされます。 非トランザクション内のコマンド**バッチ**実行済みのコマンドはロールバックされません。  
  
 通常、**キャンセル**コマンドを使用して、現在アクティブなセッションで実行中のコマンドをキャンセルします。 その場合は、none の子要素の**キャンセル**コマンドを指定する必要があります。 **キャンセル**コマンドこともできます管理者によって接続または現在アクティブなセッションを除いて、セッションの実行中のコマンドをキャンセルします。 特定のデータベースの管理者権限を持つロールのメンバーは、そのデータベースに該当する接続やセッションでのコマンドをキャンセルできます。サーバー管理者は、特定の Analysis Services インスタンスに関連した接続やセッションでのコマンドをキャンセルできます。  
  
 現在の接続やセッションに関する情報を取得する、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、インスタンス、 **Discover** 、それぞれ DISCOVER_CONNECTIONS および DISCOVER_SESSIONS スキーマ行セットを要求するメソッドを実行できます。 特定のデータベースの管理者権限を持つロールのメンバーは、DISCOVER_SESSIONS スキーマ行セットの SESSION_CURRENT_DATABASE 制限列の中でそのデータベースを指定することにより、特定のデータベースに関連したセッションだけを返すことができます。 詳細については、 **Discover**メソッドを参照してください[検出メソッド &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>参照  
 [バッチ要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
