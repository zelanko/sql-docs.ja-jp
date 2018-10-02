---
title: catalog.delete_folder (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b9c08992-500c-447e-bc19-1eb13c9b0293
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ae60521ebd4b3bf9d10e12d5f15a54ceb0166c04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626140"
---
# <a name="catalogdeletefolder-ssisdb-database"></a>catalog.delete_folder (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログからフォルダーを削除します。  
  
## <a name="syntax"></a>構文  
  
```sql  
delete_folder [ @folder_name = ] folder_name  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 削除されるフォルダーの名前。 *folder_name* は **nvarchar(128)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 フォルダーの削除を確認するメッセージが返されます。  
  
  
