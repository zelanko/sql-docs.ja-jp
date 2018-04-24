---
title: '@@MAX_PRECISION (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@MAX_PRECISION_TSQL'
- '@@MAX_PRECISION'
dev_langs:
- TSQL
helpviewer_keywords:
- precision [SQL Server], @@MAX_PRECISION
- numeric data type, precision level
- decimal data type, precision level
- '@@MAX_PRECISION function'
- data types [SQL Server], precision
ms.assetid: 9e7158a1-e503-422a-b326-3c9b06e181b2
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 344a2dd3d290a1d7e44583a4a9f1d9c28d0a6920
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="x40x40maxprecision-transact-sql"></a>&#x40;&#x40;MAX_PRECISION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用される有効桁数を返します **decimal** と **数値** データ型は、現在サーバーに設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@MAX_PRECISION  
```  
  
## <a name="return-types"></a>戻り値の型  
 **tinyint**  
  
## <a name="remarks"></a>Remarks  
 既定では、38 という最大有効桁数が返されます。  
  
## <a name="examples"></a>使用例  
  
```  
SELECT @@MAX_PRECISION AS 'Max Precision'  
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [10 進数の数値と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [有効桁数、小数点以下桁数、および長さ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)  
  
  
