---
title: CREATE WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
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
- CREATE WORKLOAD CLASSIFIER
- CREATE_WORKLOAD_CLASSIFIER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 64235b77ea2e1cf2f2c4c8d8240f34ad2e8eab8b
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090047"
---
# <a name="create-workload-classifier-transact-sql"></a>CREATE WORKLOAD CLASSIFIER (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

ワークロード管理分類子を作成します。  分類子では、受信要求がワークロード グループに割り当てられると共に、分類子ステートメントの定義に指定されたパラメーターに基づいて重要度が割り当てられます。  分類子は要求が送信されるごとに評価されます。  要求が分類子と一致しない場合、要求は既定のワークロード グループに割り当てられます。  既定のワークロード グループは、smallrc リソース クラスです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>構文

```
CREATE WORKLOAD CLASSIFIER classifier_name  
WITH  
    ( WORKLOAD_GROUP = 'name'  
     ,MEMBERNAME = 'security_account'
 [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL (default) | ABOVE_NORMAL | HIGH }])
[;]
```

## <a name="arguments"></a>引数

 *classifier_name*  
 ワークロード分類子を識別する名前を指定します。  classifier_name は sysname です。  これは長さを最大で 128 文字とすることができ、インスタンス内では一意である必要があります。

WORKLOAD_GROUP = *'name'* 分類子の規則によって条件が満たされると、name によって要求がワークロード グループにマップされます。  name は sysname です。  これは長さを最大で 128 文字とすることができ、分類子作成時には有効なワークロード グループ名とする必要があります。

WORKLOAD_GROUP は次に示す既存のリソース クラスにマップする必要があります。

|静的リソース クラス|動的リソース クラス|
|------------------------|-----------------------|
|staticrc10|smallrc|
|staticrc20|mediumrc|
|staticrc30|largerc|
|staticrc40|xlargerc|
|staticrc50||
|staticrc60||
|staticrc70||
|staticrc80||

MEMBERNAME = *'security_account'* これはロールに追加されるセキュリティ アカウントです。  security_account は sysname です。既定値はありません。 security_account は、データベース ユーザー、データベース ロール、Azure Active Directory ログイン、または Azure Active Directory グループとすることができます。

IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH } 要求の相対的な重要度を指定します。  重要度は次のいずれかです。

- LOW
- BELOW_NORMAL
- NORMAL (既定値)
- ABOVE_NORMAL
- HIGH  

重要度は要求がスケジュールされる順番に影響します。それによって、リソースおよびロックへの最初のアクセスが指定されます。

ユーザーがさまざまなリソース クラスが割り当てられた、または複数の分類子が一致する複数のロールのメンバーである場合、そのユーザーには最上位のリソース クラスが割り当てられます。 詳細については、[ワークロードの分類](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification#classification-precedence)に関するページを参照してください。

## <a name="permissions"></a>アクセス許可

 CONTROL DATABASE アクセス許可が必須です。  
  
## <a name="examples"></a>使用例

 次の例は、`wgcELTRole` という名前のワークロード分類子を作成する方法を示します。 この例では、ワークロード グループ staticrc20 およびユーザー `ELTRole` が使用され、重要度が `above_normal` に設定されています。

```sql
CREATE WORKLOAD CLASSIFIER wgcELTRole
  WITH (WORKLOAD_GROUP = 'staticrc20'
       ,MEMBERNAME = 'ELTRole'
      ,IMPORTANCE = above_normal);
```

## <a name="see-also"></a>参照

[DROP WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-classifier-transact-sql.md)</br>
カタログ ビュー [sys.workload_management_workload_classifier_details](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)</br>
カタログ ビュー [sys.workload_management_workload_classifiers](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)
[SQL Data Warehouse の分類](/azure/sql-data-warehouse/classification)
