---
title: 論理演算子 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], logical
- testing truth
- truth testing
- "TRUE"
- "FALSE"
- logical operators [SQL Server], Transact-SQL
ms.assetid: edd92f08-76fb-4fd7-a4b6-8520d6a81df1
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4447b7f120bc393f9c8a587d3c9490b59bfa809a
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36254264"
---
# <a name="logical-operators-transact-sql"></a>論理演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  論理演算子は、条件の真偽をテストします。 論理演算子は、比較演算子と同様、TRUE、FALSE、または UNKNOWN を値にとる**ブール** データ型を返します。  
  
|演算子|意味|  
|--------------|-------------|  
|[ALL](../../t-sql/language-elements/all-transact-sql.md)|すべての比較セットが TRUE の場合、TRUE を返します。|  
|[AND](../../t-sql/language-elements/and-transact-sql.md)|両方のブール式が TRUE の場合、TRUE を返します。|  
|[ANY](../../t-sql/language-elements/any-transact-sql.md)|比較セットの中の 1 つだけでも TRUE の場合、TRUE を返します。|  
|[BETWEEN](../../t-sql/language-elements/between-transact-sql.md)|オペランドが範囲内にある場合、TRUE を返します。|  
|[EXISTS](../../t-sql/language-elements/exists-transact-sql.md)|サブクエリが行を含む場合、TRUE を返します。|  
|[IN](../../t-sql/language-elements/in-transact-sql.md)|オペランドが式の 1 つに一致する場合、TRUE を返します。|  
|[LIKE](../../t-sql/language-elements/like-transact-sql.md)|オペランドがパターンに一致する場合、TRUE を返します。|  
|[NOT](../../t-sql/language-elements/not-transact-sql.md)|論理演算子の値を反転します。|  
|[OR](../../t-sql/language-elements/or-transact-sql.md)|いずれかのブール式が TRUE の場合、TRUE を返します。|  
|[SOME](../../t-sql/language-elements/some-any-transact-sql.md)|比較セットのいくつかが TRUE の場合、TRUE を返します。|  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operator-precedence-transact-sql.md)  
  
  
