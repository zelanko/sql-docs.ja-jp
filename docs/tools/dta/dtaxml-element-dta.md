---
title: DTAXML 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4eeed88249de7d3d04bee44262d72e113a8e04ec
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="dtaxml-element-dta"></a>DTAXML 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]データベース エンジン チューニング アドバイザーの XML ルート要素入力または出力ファイル、 **DTAXML**するチューニング入力と、チューニング データベース エンジン チューニング アドバイザーで生成される出力を記述するすべての要素が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|Description|  
|---------------|-----------------|  
|**xmlns:xsi**|必須。 XML Schema Instance 名前空間を識別します。 この名前空間の属性を使用して、データベース エンジン チューニング アドバイザーの XML ファイルの検証に使用するスキーマを参照します。<br /><br /> 必須値 : [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|必須。 データベース エンジン チューニング アドバイザーの名前空間を識別します。<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の XML エディターを使用してデータベース エンジン チューニング アドバイザーの XML ファイルを編集する場合、F1 ヘルプとダイナミック ヘルプでは、この値を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの参照トピックを検索します。<br /><br /> 必須値 :<br /><br /> [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?LinkId=43100) の名前空間|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|DTA の XML ファイルにつき 1 回の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|なし|  
|**子要素**|[DTAInput 要素 &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput** 要素 (詳細については、「[データベース エンジン チューニング アドバイザーの XML スキーマ](http://schemas.microsoft.com/sqlserver/)」を参照してください)|  
  
## <a name="remarks"></a>解説  
 XML 名前空間の詳細については、 [MSDN Library の「](http://go.microsoft.com/fwlink/?LinkId=7341) XML ドキュメントにおける名前空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」を参照してください。  
  
## <a name="example"></a>例  
 一般的な **DTAXML** 要素の例については、「[XML 入力ファイル サンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40; データベース エンジン チューニング アドバイザー &#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
