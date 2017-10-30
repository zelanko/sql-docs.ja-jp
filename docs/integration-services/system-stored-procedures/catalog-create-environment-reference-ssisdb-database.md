---
title: "catalog.create_environment_reference (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 496136e8a0073ba93f003d8dfa539afb48d2c5dc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  環境参照をプロジェクトの作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_location = ] reference_location  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 環境を参照しているプロジェクトのフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 環境を参照しているプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @environment_name =] *environment_name*  
 参照されている環境の名前。 *Environment_name*は**nvarchar (128)**です。  
  
 [ @reference_location =] *reference_location*  
 環境をプロジェクトと同じフォルダーに配置できるか (相対参照)、または別のフォルダーに配置できるか (絶対参照) を示します。 相対参照を指定するには、値 `R` を使用します。 絶対参照を指定するには、値 `A` を使用します。 *Reference_location*は**char (1)**です。  
  
 [ @environment_folder_name =] *environment_folder_name*  
 参照先の環境があるフォルダーの名前。 この値は絶対参照にする必要があります。 *Environment_folder_name*は**nvarchar (128)**です。  
  
 [ @reference_id =] *reference_id*  
 新しい参照の一意識別子を返します。 このパラメーターはオプションです。 *Reference_id*は**bigint**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトに対する READ および MODIFY 権限、および環境に対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   フォルダー名が無効  
  
-   プロジェクト名が無効  
  
-   ユーザーが不適切なアクセス許可  
  
-   使用して絶対参照が指定されて、`A`文字内、 *reference_location*パラメーターは、フォルダーの名前がで指定されていない、 *environment_folder_name*パラメーター。  
  
## <a name="remarks"></a>解説  
 プロジェクトでは、相対または絶対環境参照を使用できます。 相対参照では、環境を名前で参照され、プロジェクトと同じフォルダーに格納されている必要があります。 絶対参照の場合、名前とフォルダーによって環境を参照します。プロジェクトとは異なるフォルダーに格納されている環境を参照する場合があります。 プロジェクトでは複数の環境を参照できます。  
  
  

