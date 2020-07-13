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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 36485d7731d1d575eb3cff75ca19c60b13969452
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749590"
---
# <a name="catalogdelete_project-ssisdb-database"></a>catalog.delete_project (SSISDB データベース)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="remarks"></a>解説  
 対応するプロジェクトのすべてのオブジェクトおよび環境参照が、プロジェクトと共に削除されます。 ただし、プロジェクトのバージョンと関連する操作レコードは、操作のクリーンアップ ジョブが次回実行されるまで保持されます。  
  
  
