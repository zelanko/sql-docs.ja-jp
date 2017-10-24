---
title: "catalog.create_environment (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 588728b6f86090e5b8f492ba3a117e0ccd47132e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  環境を作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>引数  
 [@folder_name =] *folder_name*  
 環境を格納するフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [@environment_name =] *environment_name*  
 環境の名前。 *Environment_name*は**nvarchar (128)**です。  
  
 [@environment_description=] *environment_description*  
 省略可能な環境の説明。 *Environment_description*は**nvarchar (1024)**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   フォルダーの READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   データベース ロール (database role)  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   フォルダー名が見つからない  
  
-   指定したフォルダーには、同じ名前を持つ環境が既に存在する  
  
## <a name="remarks"></a>解説  
 環境名は、フォルダー内で一意になる必要があります。  
  
  
