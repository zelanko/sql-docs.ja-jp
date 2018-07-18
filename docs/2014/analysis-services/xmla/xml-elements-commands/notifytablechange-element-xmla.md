---
title: NotifyTableChange 要素 (XMLA) |Microsoft Docs
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
api_name:
- NotifyTableChange Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#NotifyTableChange
- http://schemas.microsoft.com/analysisservices/2003/engine#NotifyTableChange
- microsoft.xml.analysis.notifytablechange
helpviewer_keywords:
- NotifyTableChange command
ms.assetid: b76898eb-20d3-48c8-9eb8-1fd5df638bcc
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 612738591115a2e7af964ba4ee5d9950587e45bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203902"
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange 要素 (XMLA)
  インスタンスに通知[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]指定されたデータ ソース内のテーブルに対して変更が発生しました。  
  
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
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[オブジェクト](../xml-elements-properties/object-element-xmla.md)、 [TableNotifications](../xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `NotifyTableChange` コマンドを使用すると、クライアント アプリケーションは、データ ソースに含まれる 1 つ以上のテーブルの内容が変更されたことを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに明示的に通知することができます。 プロアクティブ キャッシュの場合、この通知は、それらのテーブルに基づくリレーショナル OLAP (ROLAP) オブジェクトを再確認して更新する必要があることを示します。  
  
 この通知方法は、変更内容の検出や追跡が難しいデータ ソース ビュー内で定義されたビューまたは名前付きクエリを基にした、ROLAP オブジェクトの場合に最も適しています。  
  
 `Object` 要素は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース内のデータ ソースを参照する必要があります。 データ ソース以外のオブジェクトを `Object` 要素が参照する場合、エラーが発生します。  
  
 プロアクティブ キャッシュの詳細については、「[プロアクティブ キャッシュ (パーティション)](../../multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
