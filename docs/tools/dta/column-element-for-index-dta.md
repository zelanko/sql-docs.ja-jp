---
title: Index の Column 要素 (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.openlocfilehash: 008cba36af33c465c3a126dc3e101b8ebca28e36
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307887"
---
# <a name="column-element-for-index-dta"></a>Index の Column 要素 (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

ユーザー指定の構成で、インデックスを作成する列を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
 **Type**: 省略可。 インデックスの列の種類を指定します。 この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。  
  
-   **KeyColumn**  
  
     列がインデックス キーによって参照されていることを指定します。 この属性を設定するには、以下の構文を使用します。  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     キー列の詳細については、「 [クラスター化インデックスと非クラスター化インデックスの概念](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)」を参照してください。  
  
-   **IncludedColumn**  
  
     列がキー列ではなく、付加列であることを指定します。 この属性を設定するには、以下の構文を使用します。  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     付加列の詳細については、「 [付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。  
  
 **SortOrder**: 省略可。 列の並べ替え順を指定します。 **string** データ型を使用して、 **"Ascending"** または **"Descending"** の並べ替え順のいずれかを以下のように指定します。  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**Index** 要素につき 1024 列まで指定できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Index 要素 &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**子要素**|[Column の Name 要素 &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
