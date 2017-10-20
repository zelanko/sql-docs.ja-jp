---
title: "catalog.get_project (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f263c9e4-a7db-4888-a458-70ae99b1f729
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: adb3542d50db426d5908aa8786145406d7263ad6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetproject-ssisdb-database"></a>catalog.get_project (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  配置されているプロジェクトのバイナリ ストリームを取得、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]サーバー。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.get_project [ @folder_name = ] folder_name , [ @project_name = ] project_name   
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 プロジェクトの名前。 *project_name*は**nvarchar (128)**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 プロジェクトのバイナリ ストリームとして返されます**varbinary (max)**です。 フォルダーまたはプロジェクトが見つからない場合、結果は返されません。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトに対する読み取り権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 次の一覧には、エラーが発生する get_project ストアド プロシージャが可能性がある条件について説明します。  
  
-   プロジェクトが存在しない  
  
-   フォルダーが存在しない  
  
-   ユーザーに適切な権限がない  
  
  
