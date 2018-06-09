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
ms.openlocfilehash: 049756318b4d0e14b0bd2fe858d7a2153673cfd5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575004"
---
# <a name="notifytablechange-element-xmla"></a>NotifyTableChange 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  指定されたデータ ソース内のテーブルの内容が変更されたことを Analysis Services のインスタンスに通知します。  
  
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
  
## <a name="remarks"></a>コメント  
 **NotifyTableChange**コマンドを使用して、クライアント アプリケーションに明示的に通知を[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]はいずれかのインスタンスまたはデータ ソースに含まれる複数のテーブルが変更されました。 プロアクティブ キャッシュの場合、この通知は、それらのテーブルに基づくリレーショナル OLAP (ROLAP) オブジェクトを再確認して更新する必要があることを示します。  
  
 この通知方法は、変更内容の検出や追跡が難しいデータ ソース ビュー内で定義されたビューまたは名前付きクエリを基にした、ROLAP オブジェクトの場合に最も適しています。  
  
 **オブジェクト**要素でデータ ソースを参照する必要があります、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素を参照し、データ ソース以外のオブジェクト、エラーが発生します。  
  
 プロアクティブ キャッシュの詳細については、「[プロアクティブ キャッシュ (パーティション)](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。  
  
## <a name="see-also"></a>参照
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
