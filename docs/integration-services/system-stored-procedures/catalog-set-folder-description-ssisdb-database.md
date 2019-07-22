---
title: catalog.set_folder_description (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 802416f6-5177-4db5-bca5-976dec5faf53
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ac7a747ea5f63e20d2f76b59541a13ff98d1419c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038685"
---
# <a name="catalogsetfolderdescription-ssisdb-database"></a>catalog.set_folder_description (SSISDB データベース)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーの説明を設定します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_folder_description [ @folder_name = ] folder_name  
    , [ @folder_description = ] folder_description  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 フォルダーの名前。 *folder_name* は **nvarchar(128)** です。  
  
 [ @folder_description = ] *folder_description*  
 フォルダーの説明。 *Folder_description* は **nvarchar (max)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャは、新しいフォルダーの説明の設定を確認するメッセージを返します。  
  
  
