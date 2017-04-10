---
title: "文字列の余白 (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "余白文字列 [Integration Services]"
  - "式 [Integration Services], 文字列の埋め込み"
  - "文字列の余白"
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# 文字列の余白 (SSIS)
  式エバリュエーターは、文字列の先頭および末尾にスペースが含まれているかどうかをチェックしません。また、文字列を比較する前に、比較文字列の長さが同じになるように文字列を埋め込む処理も行いません。 式に文字列の余白が必要な場合、+ 演算子を使用して列の値と空白の文字列を連結できます。 詳細については、「[+ &#40;連結&#41; &#40;SSIS 式&#41;](../../integration-services/expressions/concatenate-ssis-expression.md)」を参照してください。  
  
 これに対し、スペースを削除する場合、式エバリュエーターで用意されている LTRIM、RTRIM、および TRIM 関数を使用して、先頭または末尾のスペース、またはその両方を削除できます。 詳細については、「[LTRIM &#40;SSIS 式&#41;](../../integration-services/expressions/ltrim-ssis-expression.md)」、「[RTRIM &#40;SSIS 式&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)」、および「[TRIM &#40;SSIS 式&#41;](../../integration-services/expressions/trim-ssis-expression.md)」を参照してください。  
  
> [!NOTE]  
>  LEN 関数は、先頭と末尾の空白を含めてカウントします。  
  
## 関連コンテンツ  
 pragmaticworks.com の技術記事「 [SSIS 式チート シート](http://go.microsoft.com/fwlink/?LinkId=746575)」  
  
  