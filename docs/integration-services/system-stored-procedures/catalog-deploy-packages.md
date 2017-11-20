---
title: "catalog.deploy_packages |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1839430dd7fb83ab16c4de46011819e3ce28e835
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeploypackages"></a>catalog.deploy_packages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  内のフォルダーを 1 つまたは複数のパッケージを配置、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログまたは以前に配置されている既存のパッケージを更新します。  
  
## <a name="syntax"></a>構文  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 フォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 フォルダー、プロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @packages_table =] *packages_table*  
 バイナリ コンテンツ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)](.dtsx) ファイルをパッケージ化します。 *Packages_table*は**[カタログ]. [Package_Table_Type]**  
  
 [ @operation_id =] *operation_id*  
 配置操作の一意識別子を返します。 *Operation_id*は**bigint**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトまたはパッケージを更新するパッケージの変更のアクセス許可に対する CREATE_OBJECTS 権限、します。  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 このストアド プロシージャがエラーを発生させる可能性がある条件を以下に示します。  
  
-   パラメーターが存在しないオブジェクトを参照、パラメーターが、既に存在するオブジェクトを作成しようとしています。 または、パラメーターは他の方法では無効です。  
  
-   ユーザーに十分な権限がない  
  
  

