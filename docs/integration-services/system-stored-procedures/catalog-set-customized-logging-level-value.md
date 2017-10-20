---
title: "catalog.set_customized_logging_level_value |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: d83fb763-c7c6-4e20-bd10-0f995598b198
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75ef405fe4550e81ec2d5178a1d3242d405755af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedlogginglevelvalue"></a>catalog.set_customized_logging_level_value
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  統計情報、または既存のログ記録のカスタマイズされたレベルで記録されたイベントを変更します。 カスタマイズされたログ記録レベルの詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="syntax"></a>構文  
  
```sql  
set_customized_logging_level_value [ @level_name = ] level_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
  
```  
  
## <a name="arguments"></a>引数  
 [ @level_name =] *level_name*  
 既存の名前は、ログ記録レベルをカスタマイズします。  
  
 *Level_name*は**nvarchar (128)**です。  
  
 [ @property_name =] *property_name*  
 変更するプロパティの名前。 有効な値は**プロファイル**と**イベント**です。  
  
 *Property_name*は**nvarchar (128)**です。  
  
 [ @property_value =] *property_value*  
 指定した指定したプロパティの新しい値では、ログ記録レベルをカスタマイズします。  
  
 プロファイルとイベントの有効な値の一覧は、次を参照してください。 [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md)です。  
  
 *Property_value*は、 **bigint**です。  
  
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
  
  
