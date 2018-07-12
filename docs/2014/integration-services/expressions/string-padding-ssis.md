---
title: 文字列の余白 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b95eed3c086b0d9e07feb11c353e90cece56a18e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152883"
---
# <a name="string-padding-ssis"></a>文字列の余白 (SSIS)
  式エバリュエーターは、文字列の先頭および末尾にスペースが含まれているかどうかをチェックしません。また、文字列を比較する前に、比較文字列の長さが同じになるように文字列を埋め込む処理も行いません。 式に文字列の余白が必要な場合、+ 演算子を使用して列の値と空白の文字列を連結できます。 詳細については、「[+ &#40;連結&#41; &#40;SSIS 式&#41;](concatenate-ssis-expression.md)」を参照してください。  
  
 これに対し、スペースを削除する場合、式エバリュエーターで用意されている LTRIM、RTRIM、および TRIM 関数を使用して、先頭または末尾のスペース、またはその両方を削除できます。 詳細については、「[LTRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)」、「[RTRIM &#40;SSIS 式&#41;](rtrim-ssis-expression.md)」、および「[TRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)」を参照してください。  
  
> [!NOTE]  
>  LEN 関数は、先頭と末尾の空白を含めてカウントします。  
  
## <a name="related-content"></a>関連コンテンツ  
 pragmaticworks.com の技術記事「 [SSIS 式チート シート](http://go.microsoft.com/fwlink/?LinkId=217683)」  
  
  
