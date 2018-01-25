---
title: "modify() メソッド (xml データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 429797447e56ecb57f0dc257bfd13bea59ea1f40
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="modify-method-xml-data-type"></a>modify() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML ドキュメントのコンテンツを変更します。 内容を変更するには、このメソッドを使用して、 **xml**型の変数または列。 このメソッドは XML DML ステートメントを使用して、XML データのノードの挿入、更新、削除を行います。 **Modify()**のメソッド、 **xml**データ型は、UPDATE ステートメントの SET 句でのみ使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>引数  
 XML_DML  
 XML DML (データ操作言語) の文字列です。 XML ドキュメントは、この表記に従って更新されます。  
  
> [!NOTE]  
>  場合、エラーが返されます、 **modify()**メソッドまたは null 値で呼び出されますが、結果が null の値。  
  
## <a name="examples"></a>使用例  
 **Modify()**メソッドには、文字列で、XML データ操作言語 (DML)、用のサンプルが必要です。 **modify()** XML DML ステートメントを説明するトピックに含まれています。 これらの例については、次を参照してください。 [insert &#40;です。XML DML&#41;](../../t-sql/xml/insert-xml-dml.md)、[削除 &#40;です。XML DML&#41;](../../t-sql/xml/delete-xml-dml.md)と[の値 &#40; を置き換えますXML DML&#41;](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>参照  
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
