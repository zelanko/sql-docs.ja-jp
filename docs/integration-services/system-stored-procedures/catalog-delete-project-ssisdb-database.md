---
title: catalog.delete_project (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: f3431445-8dd2-443b-813e-b99db893977e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7cc535ec472bc3258989ed6268be17228f7dc8d7
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290858"
---
# <a name="catalogdeleteproject-ssisdb-database"></a>catalog.delete_project (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーから既存のプロジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.delete_project [ @folder_name = ] folder_name , [ @project_name = ] project_name  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *folder_name* は **nvarchar(128)** です。  
  
 [ @project_name = ] *project_name*  
 削除されるプロジェクトの名前。 *project_name* は **nvarchar(128)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 次の一覧は、delete_project ストアド プロシージャにエラーを発生させる可能性があるいくつかの条件を以下に示します。  
  
-   プロジェクトが存在しない  
  
-   フォルダーが存在しない  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>Remarks  
 対応するプロジェクトのすべてのオブジェクトおよび環境参照が、プロジェクトと共に削除されます。 ただし、プロジェクトのバージョンと関連する操作レコードは、操作のクリーンアップ ジョブが次回実行されるまで保持されます。  
  
  
