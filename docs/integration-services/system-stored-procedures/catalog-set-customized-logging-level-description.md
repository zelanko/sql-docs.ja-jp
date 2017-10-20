---
title: "catalog.set_customized_logging_level_description |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3899e02c6b1eaa2cc76ad4411d9be3aded817728
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedloggingleveldescription"></a>catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  既存のカスタマイズされたログ記録レベルの説明を変更します。 カスタマイズされたログ記録レベルの詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="syntax"></a>構文  
  
```sql  
set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
  
```  
  
## <a name="arguments"></a>引数  
 [ @level_name =] *level_name*  
 既存の名前は、ログ記録レベルをカスタマイズします。  
  
 *Level_name*は**nvarchar (128)**です。  
  
 [ @level_description =] *level_description*  
 指定した新しい説明では、ログ記録レベルをカスタマイズできます。  
  
 *Level_description*は**nvarchar (1024)**です。  
  
## <a name="remarks"></a>解説  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーには、必要なアクセス許可がありません。  
  
  
