---
title: "catalog.clear_object_parameter_value (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5d0d89081a31341a8d813d9985940c0e3ce0160a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogclearobjectparametervalue-ssisdb-database"></a>catalog.clear_object_parameter_value (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存のパラメーターの値をクリア[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]プロジェクトまたはパッケージをサーバーに格納されています。  
  
## <a name="syntax"></a>構文  
  
```sql  
clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 プロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @object_type =] *object_type*  
 オブジェクトの種類。 有効な値は、プロジェクトでは `20`、パッケージでは `30` です。 *Object_type*は**smallInt**です。  
  
 [オブジェクト名 (_n) @ =]*オブジェクト名 (_n)*  
 パッケージの名前です。 *オブジェクト名 (_n)*は**nvarchar (260)**です。  
  
 [@parameter_名前 =] *parameter_name*  
 パラメーターの名前。 *Parameter _ 名前*は**nvarchar (128)**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 次に、エラーが発生する clear_object_parameter ストアド プロシージャが可能性がある条件を説明します。  
  
-   無効なオブジェクトの種類が指定されているか、またはオブジェクト名がプロジェクトで見つからない  
  
-   プロジェクトが存在しない、プロジェクトにアクセスできない、またはプロジェクト名が無効  
  
-   無効なパラメーター値が指定されている  
  
-   ユーザーには、適切なアクセス許可がありません。  
  
  
