---
title: "catalog.rename_customized_logging_level |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b1a57d5e-3f03-4901-8b2b-bb8b371b595b
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 00c2cd8fa5f8423a7791d663d02aecbf27b8ab41
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenamecustomizedlogginglevel"></a>catalog.rename_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  既存のカスタマイズされたログ記録レベルの名前を変更します。 カスタマイズされたログ記録レベルの詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.rename_customized_logging_level [ @old_name = ] old_name  
    , [ @new_name = ] new_name  
```  
  
## <a name="arguments"></a>引数  
 [ @old_name =]*古い名前*  
 既存の名前は、名前を変更するログ記録レベルをカスタマイズします。  
  
 *古い名前*は**nvarchar (128)**です。  
  
 [ @new_name =] *new_name*  
 指定した新しい名前では、ログ記録レベルをカスタマイズします。  
  
 *New_name*は**nvarchar (128)**です。  
  
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
  
  
