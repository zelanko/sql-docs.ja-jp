---
title: xp_sprintf (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 01/09/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sprintf_TSQL
- xp_sprintf
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sprintf
ms.assetid: 1eedd65c-03cc-4eab-b76e-04684fdfec52
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ba1648da108762b03155eb93e1ee11c53a75583
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "75831763"
---
# <a name="xp_sprintf-transact-sql"></a>xp_sprintf (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  文字列の出力パラメーターに一連の文字および値を書式設定して格納します。 各フォーマット引数は対応する引数に置き換えられます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_sprintf { string OUTPUT , format }  
     [ , argument [ ,...n ] ]  
```  
  
## <a name="arguments"></a>引数  
 *文字列*  
 出力を受け取る**varchar**変数を示します。  
  
 OUTPUT  
 指定すると、変数の値が出力パラメーターに格納されます。  
  
 *形式*  
 は、C 言語の**sprintf**関数でサポートされているものと同様に、*引数*の値のプレースホルダーを含む書式指定文字列です。 現在、% s 書式引数のみがサポートされています。  
  
 *引数*  
 対応するフォーマット引数の値を表す文字列。  
  
 *n*  
 は、最大で50個の引数を指定できることを示すプレースホルダーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 **xp_sprintf**は次のメッセージを返します。  
  
 `The command(s) completed successfully.`  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の一般的な拡張ストアドプロシージャ](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_sscanf &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/xp-sscanf-transact-sql.md)  
  
  
