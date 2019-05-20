---
title: catalog.create_folder (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a5115d9c66dd7baf091635b06ff413aa8c4ca736
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65716905"
---
# <a name="catalogcreatefolder-ssisdb-database"></a>catalog.create_folder (SSISDB データベース)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーを作成します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_folder [@folder_name =] folder_name, [@folder_id =] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [@folder_name =] *folder_name*  
 新しいフォルダーの名前です。 *folder_name* は **nvarchar(128)** です。  
  
 [@folder_name =] *folder_id*  
 フォルダーの一意識別子 (ID)。 *folder_id* は **bigint** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 フォルダーの識別子が返されます。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
同じ名前のフォルダーが既に存在する場合、ストアド プロシージャはエラーを返します。  
  
  
