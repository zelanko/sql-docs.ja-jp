---
title: ReportAction データ型 (ASSL) |Microsoft ドキュメント
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
- ReportAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportAction
helpviewer_keywords:
- ReportAction data type
ms.assetid: b22f0d52-ed3a-4239-840e-0eaf172d7276
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7c2c5140f3d2723f0456b007bc9228c5f87bbaa6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076304"
---
# <a name="reportaction-data-type-assl"></a>ReportAction データ型 (ASSL)
  生成するアクションを表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]レポートします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ReportAction>  
   <!-- The following elements extend Action -->  
   <ReportServer>...</ReportServer>  
   <Path>...</Path>  
   <ReportParameters>...</ReportParameters>  
   <ReportFormatParameters>...</ReportFormatParameters>  
</ReportAction>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[操作](action-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[パス](../properties/path-element-assl.md)、 [ReportFormatParameters](../collections/reportformatparameters-element-assl.md)、 [ReportParameters](../collections/reportparameters-element-assl.md)、 [ReportServer](../objects/server-element-assl.md)|  
|派生要素|[アクション](../objects/action-element-assl.md)([アクション](../collections/actions-element-assl.md)のコレクション[キューブ](../objects/cube-element-assl.md)または[パースペクティブ](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 レポート サーバーは、レポートに関する URL ベースの要求に応答します。 型を持つレポート アクションが定義されている*レポート*です。 リソースおよびパラメーターは、アクションの作成時にサーバーに送信されます。 サーバーは、rowset 型のアクションとしてアクションを公開します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ReportAction>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  