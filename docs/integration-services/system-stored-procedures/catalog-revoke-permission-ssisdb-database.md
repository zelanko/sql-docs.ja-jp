---
title: "catalog.revoke_permission (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- revoke_permission stored procedure [Integration Services]
- catalog.revoke_permission stored procedure [Integration Services]
ms.assetid: 850b9c26-5c7c-47b9-a61c-5cf9bb5948cf
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f058368bdd39b31a569d8810cccfc4d03d9f875e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrevokepermission-ssisdb-database"></a>catalog.revoke_permission (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  セキュリティ保護可能なオブジェクトに対する権限を取り消します、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```  
  
revoke_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>引数  
 [ @object_type =] *object_type*  
 セキュリティ保護可能なオブジェクトの種類。 セキュリティ保護可能なオブジェクトの種類を含めるフォルダー (`1`)、プロジェクト (`2`)、環境 (`3`)、および操作 (`4`)。*Object_type*は**smallint***です。*  
  
 [ @object_id =] *object_id*  
 一意識別子 (ID) のセキュリティ保護可能なオブジェクトです。 *Object_id*は**bigint**です。  
  
 [ @principal_id =] *principal_id*  
 権限を取り消すプリンシパルの ID。 *Principal_id*は**int**です。  
  
 [ @permission_type =] *permission_type*  
 権限の種類。 *Permission_type*は**smallint**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を返します。  
  
 1 (object_class は有効ではありません)  
  
 2 (object_id が存在しない)  
  
 3 (プリンシパルが存在しない)  
  
 4 (アクセス許可は、無効です)  
  
 その他のエラーの場合は 5 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   オブジェクトに対する ASSIGN_PERMISSIONS 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="remarks"></a>解説  
 Permission_type が指定されている場合、ストアド プロシージャは、オブジェクトのプリンシパルに明示的に割り当てられているアクセス許可を削除します。 このようなインスタンスがない場合でも、プロシージャは成功コード値 (`0`) を返します。 Permission_type を省略すると、ストアド プロシージャは、プリンシパル オブジェクトへのすべてのアクセス許可を削除します。  
  
> [!NOTE]  
>  プリンシパルが、指定したアクセス権限を持つロールのメンバーの場合、プリンシパルは、オブジェクトに対して指定した権限を持つ場合があります。  
  
 このストアド プロシージャを使用すると、次の表に記載されている権限の種類を取り消すことができます。  
  
|permission_type 値|権限名|権限の説明|該当するオブジェクトの種類|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが読み取ることができるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトのコンテンツを列挙したり、読み取ったりすることはできません。|フォルダー、プロジェクト、環境、操作|  
|`2`|MODIFY|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが変更できるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトを修正することはできません。|フォルダー、プロジェクト、環境、操作|  
|`3`|CREATE ステートメントを実行する前に、|プリンシパルがプロジェクトのすべてのパッケージを実行できるようにします。|プロジェクト|  
|`4`|MANAGE_PERMISSIONS|プリンシパルがオブジェクトに権限を割り当てることができるようにします。|フォルダー、プロジェクト、環境、操作|  
|`100`|CREATE_OBJECTS|プリンシパルがフォルダーでオブジェクトを作成できるようにします。|フォルダー|  
|`101`|READ_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを読み取ることができるようにします。|フォルダー|  
|`102`|MODIFY_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを変更できるようにします。|フォルダー|  
|`103`|EXECUTE_OBJECTS|プリンシパルがフォルダーのすべてのプロジェクトからすべてのパッケージを実行できるようにします。|フォルダー|  
|`104`|MANAGE_OBJECT_PERMISSIONS|プリンシパルがフォルダー内のすべてのオブジェクトに対する権限を管理できるようにします。|フォルダー|  
  
  
