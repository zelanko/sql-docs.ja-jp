---
title: "NotifyTableChange 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: NotifyTableChange Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords: NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 220a8ceeb2f4061d3da7a8243247a8daa6818650
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]インスタンスに通知[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]指定されたデータ ソース内のテーブルに変更が発生したことです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
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
|子要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、 [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **NotifyTableChange**コマンドを使用して、クライアント アプリケーションに明示的に通知を[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はいずれかのインスタンスまたはデータ ソースに含まれる複数のテーブルが変更されました。 プロアクティブ キャッシュの場合、この通知は、それらのテーブルに基づくリレーショナル OLAP (ROLAP) オブジェクトを再確認して更新する必要があることを示します。  
  
 この通知方法は、変更内容の検出や追跡が難しいデータ ソース ビュー内で定義されたビューまたは名前付きクエリを基にした、ROLAP オブジェクトの場合に最も適しています。  
  
 **オブジェクト**要素でデータ ソースを参照する必要があります、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素を参照し、データ ソース以外のオブジェクト、エラーが発生します。  
  
 プロアクティブ キャッシュの詳細については、「[プロアクティブ キャッシュ (パーティション)](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
