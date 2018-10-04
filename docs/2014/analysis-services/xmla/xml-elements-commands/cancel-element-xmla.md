---
title: Cancel 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cancel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords:
- Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b106806118649d35e7be239b4ceea7201f349d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055212"
---
# <a name="cancel-element-xmla"></a>Cancel 要素 (XMLA)
  現在実行中のコマンドを取り消します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
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
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[CancelAssociated](../xml-elements-properties/cancelassociated-element-xmla.md)、 [ConnectionID](../xml-elements-properties/id-element-xmla.md)、 [SessionID](../xml-elements-properties/sessionid-element-xmla.md)、 [SPID](../xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Cancel` コマンドは、セッションのコンテキスト内で現在実行中のコマンドを取り消します。 クライアント アプリケーションがセッションをまだ要求していない場合は、コマンドをキャンセルできません。  
  
 `Cancel` コマンドの実行中に `Batch` コマンドが実行された場合、`Batch` コマンド全体が取り消されます。 `Batch` コマンドがトランザクション型であれば、その `Batch` コマンドに含まれるすべてのコマンドはロールバックされます。 `Batch` コマンドがトランザクション型でなければ、その `Batch` コマンドに含まれるコマンドのうち、`Cancel` コマンド実行時に実行中であったコマンドだけがロールバックされます。 非トランザクション型の `Batch` コマンド内の実行済みのコマンドは、ロールバックされません。  
  
 通常、`Cancel` コマンドは、現在アクティブなセッション上の実行中のコマンドを取り消すために使用されます。 その場合、`Cancel` コマンドの子要素を指定しないでください。 さらに、管理者は、現在アクティブなセッション以外の接続やセッションで実行中のコマンドを取り消すために `Cancel` コマンドを使用することもできます。 特定のデータベースの管理者権限を持つロールのメンバーは、そのデータベースに該当する接続やセッションでのコマンドをキャンセルできます。サーバー管理者は、特定の Analysis Services インスタンスに関連した接続やセッションでのコマンドをキャンセルできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの現在の接続やセッションに関する情報を取得するには、`Discover` メソッドを実行して、それぞれ DISCOVER_CONNECTIONS および DISCOVER_SESSIONS スキーマ行セットを要求することができます。 特定のデータベースの管理者権限を持つロールのメンバーは、DISCOVER_SESSIONS スキーマ行セットの SESSION_CURRENT_DATABASE 制限列の中でそのデータベースを指定することにより、特定のデータベースに関連したセッションだけを返すことができます。 詳細については、`Discover`メソッドを参照してください[Discover メソッド&#40;XMLA&#41;](../xml-elements-methods-discover.md)します。  
  
## <a name="see-also"></a>参照  
 [要素をバッチ&#40;XMLA&#41;](batch-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
