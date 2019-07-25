---
title: DROP WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 92e853a1d54c91b43d166555162f77030e07b9e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072029"
---
# <a name="drop-workload-classifier-transact-sql"></a>DROP WORKLOAD CLASSIFIER (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

既存のユーザー定義のワークロード管理分類子を削除します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>構文  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>引数

*classifier_name*  
ワークロード分類子を識別する名前を指定します。  classifier_name は sysname です。  これは長さを最大で 128 文字とすることができ、インスタンス内では一意である必要があります。
  
## <a name="remarks"></a>Remarks

DROP WORKLOAD CLASSIFIER ステートメントは、システム ワークロード分類子に対しては使用できません。

要求が実行されている場合、または要求キュー内で中断状態にある場合、要求の分類は維持されるので、分類子をすぐに削除することができます。  重要度が異なる分類子を削除および再作成することは、既に分類済みの要求に影響しません。

## <a name="permissions"></a>アクセス許可

CONTROL DATABASE アクセス許可が必須です。  
  
## <a name="examples"></a>使用例

次の例では、`wgcELTROLE` という名前のワークロード分類子が削除されます。  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> 送信された要求に一致する分類子が存在しない場合、それは既定のワークロード グループに分類されます。  既定のワークロード グループは、smallrc リソース クラスです。
  
## <a name="see-also"></a>参照

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[SQL Data Warehouse のワークロード分類](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
