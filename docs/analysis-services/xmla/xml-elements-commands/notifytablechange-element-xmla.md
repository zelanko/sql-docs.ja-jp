---
title: NotifyTableChange 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b379fde8b0561af0af41cabcef1b91adf459a26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  インスタンスに通知[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]指定されたデータ ソース内のテーブルに変更が発生したことです。  
  
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
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、 [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **NotifyTableChange**コマンドを使用して、クライアント アプリケーションに明示的に通知を[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はいずれかのインスタンスまたはデータ ソースに含まれる複数のテーブルが変更されました。 プロアクティブ キャッシュの場合、この通知は、それらのテーブルに基づくリレーショナル OLAP (ROLAP) オブジェクトを再確認して更新する必要があることを示します。  
  
 この通知方法は、変更内容の検出や追跡が難しいデータ ソース ビュー内で定義されたビューまたは名前付きクエリを基にした、ROLAP オブジェクトの場合に最も適しています。  
  
 **オブジェクト**要素でデータ ソースを参照する必要があります、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素を参照し、データ ソース以外のオブジェクト、エラーが発生します。  
  
 プロアクティブ キャッシュの詳細については、「[プロアクティブ キャッシュ (パーティション)](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
