---
title: catalog.delete_customized_logging_level | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 0aec1e34-f30b-4e5f-bba1-c26665cf2da6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2d7db61c085f6ac085ce0585428d43cffcdb66cd
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913127"
---
# <a name="catalogdelete_customized_logging_level"></a>catalog.delete_customized_logging_level 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

  既存のカスタマイズされたログ記録レベルを削除します。 カスタマイズされたログ記録レベルの詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.delete_customized_logging_level [ @level_name = ] level_name
```  
  
## <a name="arguments"></a>引数  
 [ @level_name = ] *level_name*  
 既存の名前はカスタマイズを削除するログ記録レベルです。  
  
 *level_name* は **nvarchar(128)** です。  
  
## <a name="remarks"></a>解説  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーには、必要なアクセス許可がありません。  
  
  
