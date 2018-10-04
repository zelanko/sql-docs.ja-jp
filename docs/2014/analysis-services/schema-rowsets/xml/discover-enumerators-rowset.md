---
title: DISCOVER_ENUMERATORS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_ENUMERATORS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b6a41d91bb5d7f5d44c362733ccbb038f707024
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218965"
---
# <a name="discoverenumerators-rowset"></a>DISCOVER_ENUMERATORS 行セット
  特定のデータ ソースの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている列挙子の名前、データ型、および列挙値の一覧を返します。 XMLA プロバイダーは、認識できるすべての列挙定数をパブリッシュします。  
  
 呼び出す場合、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_ENUMERATORS`列挙値、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します。、`DISCOVER_ENUMERATORS`スキーマ行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 列挙子ごとに複数の要素があり、各要素は列挙内の各値に対応しています。 各列挙子を表す行セットはフラットであり、列挙子の名前は同じ列挙に所属する要素に対して重複して使用される場合があります。  
  
 `DISCOVER_ENUMERATORS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`EnumName`|`DBTYPE_WSTR`||値のセットが含まれている列挙子の名前。|  
|`EnumDescription`|`DBTYPE_WSTR`||列挙子のローカライズ可能な説明。 `NULL`します。|  
|`EnumType`|`DBTYPE_WSTR`||列挙値のデータ型。|  
|`ElementName`|`DBTYPE_WSTR`||列挙子セット内のいずれかの値要素の名前。<br /><br /> 例: `TDP`|  
|`ElementDescription`|`DBTYPE_WSTR`||(省略可) 要素のローカライズ可能な説明。 `NULL`します。|  
|`ElementValue`|`DBTYPE_WSTR`||要素の値です。 `NULL`します。<br /><br /> 例: `01`|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_ENUMERATORS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`EnumName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
