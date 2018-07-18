---
title: catalog.set_environment_variable_property (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: c1deb31e-b8d1-44ca-b355-570959bc6478
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 504d0603a31e2ac5a90e2494002625daea89dd84
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331686"
---
# <a name="catalogsetenvironmentvariableproperty-ssisdb-database"></a>catalog.set_environment_variable_property (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの環境変数のプロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_environment_variable_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 環境を含むフォルダーの名前です。 *folder_name* は **nvarchar(128)** です。  
  
 [ @environment_name = ] *environment_name*  
 環境の名前。 *Environment_name* は **nvarchar(128)** です。  
  
 [ @variable_name = ] *variable_name*  
 環境変数の名前。 *variable_name* は **nvarchar(128)** です。  
  
 [ @property_name = ] *property_name*  
 環境変数プロパティの名前。 *Property_name* は **nvarchar(128)** です。  
  
 [ @property_value = ] *property_value*  
 環境変数プロパティの値。 *property_value* は **nvarchar (4000)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   環境の READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   フォルダー名が無効  
  
-   環境名が無効  
  
-   環境変数名が無効  
  
-   環境変数プロパティの名前が無効  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>Remarks  
 このリリースで設定できるのは `Description` プロパティだけです。 `Description` プロパティのプロパティ値は 4,000 文字を超えることはできません。  
  
  
