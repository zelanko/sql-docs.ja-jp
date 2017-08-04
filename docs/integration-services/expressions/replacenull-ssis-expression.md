---
title: "REPLACENULL (SSIS 式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b99a726d050dc2235f653061295e5f0829e93150
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="replacenull-ssis-expression"></a>REPLACENULL (SSIS 式)
  1 番目の式パラメーターの値が NULL の場合、2 番目の式パラメーターの値を返します。NULL でない場合は、1 番目の式の値を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a>引数  
 *expression 1*  
 この式の結果が NULL かどうかを調べます。  
  
 *expression 2*  
 1 番目の式が NULL と評価される場合、この式の結果が返されます。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
  
-   *expression 2* の長さは 0 にできます。  
  
-   いずれかの引数が NULL の場合、REPLACENULL は NULL を返します。  
  
-   BLOB 列 (DT_TEXT、DT_NTEXT、DT_IMAGE) は、いずれのパラメーターとしてもサポートされていません。  
  
-   2 つの式は、戻り値の型が同じであるものと想定されています。 同じでない場合は、2 番目の式が 1 番目の式の戻り値の型にキャストされ、データ型に互換性がない場合はエラーが発生する可能性があります。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、データベース列の NULL 値を、文字列 (1900-01-01) に置き換えます。 この関数は、特に、NULL 値を他のなんらかの値に置き換える必要のある一般的な派生列パターンで使用されます。  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  次の例で実行された方法を示しています。 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] /[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]です。  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? “1900-01-01” : MyColumn)   
```  
  
  
