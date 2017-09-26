---
title: "catalog.restore_project (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 23074fc664591411666315036e3493e1b7b26134
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  プロジェクトの復元、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]以前のバージョンのカタログ。  
  
## <a name="syntax"></a>構文  
  
```tsql  
restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [@project名 (_n) =] *project_name*  
 プロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @object_version_lsn =] *object_version_lsn*  
 プロジェクトのバージョン。 *Object_version_lsn*は**bigint**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 プロジェクトの詳細として返されます**varbinary (max)**場合、結果セットの一部として、 *project_name*が見つかった。  
  
 **NO RESULT SET**プロジェクトを指定したフォルダーに復元できないかどうかが返されます。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   プロジェクトのバージョンが存在しないか、プロジェクト名と一致しない  
  
-   プロジェクトが存在しない  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>解説  
 プロジェクトを復元すると、すべてのパラメーターが既定値としてが割り当てられ、すべての環境参照は変更されないままになります。 カタログに保持されているプロジェクトのバージョンの最大数はカタログのプロパティで決まります**MAX_VERSIONS_PER_PROJECT**のように、 [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)ビュー。  
  
> [!WARNING]  
>  プロジェクトの復元後は、環境参照が有効ではなくなる場合があります。  
  
  
