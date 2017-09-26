---
title: "catalog.move_project (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5b091ccea1f733ebbf6e52308d17c7bdb7449cbe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveproject---ssisdb-database"></a>catalog.move_project - SSISDB データベース
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  プロジェクトを内の別の 1 つのフォルダーに移動、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```tsql  
move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>引数  
 [ @source_folder =] *source_folder*  
 プロジェクトが、移動前に配置されていたソース フォルダーの名前。 *Source_folder*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 移動されるプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @destination_folder =] *destination_folder*  
 プロジェクトが移動後に配置される移動先フォルダーの名前。 *Destination_folder*は**nvarchar (128)**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   移動するプロジェクトに対する READ および MODIFY 権限と、移動先フォルダーに対する CREATE_OBJECTS 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 このストアド プロシージャがエラーを発生させる可能性がある条件を以下に示します。  
  
-   プロジェクトが存在しない  
  
-   移動元フォルダーが存在しない  
  
-   移動先フォルダーが存在しないか、移動先フォルダーに同じ名前のプロジェクトが既にある  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>解説  
 プロジェクトを元のフォルダーから目的のフォルダーに移動すると、ソース フォルダーのプロジェクトと、対応する環境参照が削除されます 移動先のフォルダーには、同じプロジェクトと環境参照が作成されます。 相対環境参照は、移動後、別のフォルダーに解決されます。 絶対参照は、移動後、同じフォルダーに解決されます。  
  
> [!NOTE]  
>  プロジェクトでは、相対または絶対環境参照を使用できます。 相対参照の場合、名前によって環境を参照します。この環境はプロジェクトと同じフォルダーに格納されている必要があります。 絶対参照の場合、名前とフォルダーによって環境を参照します。これらの参照は、プロジェクトとは異なるフォルダーに格納されている環境を参照する場合があります。  
  
  
