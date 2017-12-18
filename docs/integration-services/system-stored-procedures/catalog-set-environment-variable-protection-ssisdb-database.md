---
title: "catalog.set_environment_variable_protection (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 005b6b2f-a5d9-4ea4-8d4e-beed6ab33c0d
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba92aca58744a652314630f786ea6783e51b1cbb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogsetenvironmentvariableprotection-ssisdb-database"></a>catalog.set_environment_variable_protection (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの環境変数のセンシティビティ ビットを設定します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_environment_variable_protection [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @is_sensitive = ] is_sensitive  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 環境を含むフォルダーの名前です。 *folder_name* は **nvarchar(128)** です。  
  
 [ @environment_name = ] *environment_name*  
 環境の名前。 *environment_name* は **nvarchar(128)** です。  
  
 [ @variable_name = ] *variable_name*  
 環境変数の名前。 *variable_name* は **nvarchar(128)** です。  
  
 [ @sensitive = ] *sensitive*  
 変数がセンシティブ値を含むかどうかを示します。 値 `1` を使用すると、環境変数の値がセンシティブであることを示し、値 `0` を使用するとセンシティブではないことを示します。 センシティブ値が格納される場合、その値は暗号化されます。 センシティブでない値は、プレーンテキストで格納されます。 *sensitive* パラメーターは **bit** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   環境の READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   フォルダー名が無効  
  
-   環境名が無効  
  
-   環境変数名が無効  
  
-   ユーザーに適切な権限がない  
  
  
