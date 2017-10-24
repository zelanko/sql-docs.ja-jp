---
title: "catalog.deploy_project (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2e3439b4-7226-4b61-a993-7a1d161eac7e
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 5682cd23cb65e097bccb8cc69d5f2ec88ece7709
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogdeployproject-ssisdb-database"></a>catalog.deploy_project (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーにプロジェクトを配置するか、以前に配置した既存のプロジェクトを更新します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.deploy_project [@folder_name =] folder_name   
      , [@project_name =] project_name   
      , [@project_stream =] projectstream   
    [ , [@operation_id ] = operation_id OUTPUT ]   
```  
  
## <a name="arguments"></a>引数  
 [@folder_name =] *folder_name*  
 プロジェクトの配置先フォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [@project_name =] *project_name*  
 フォルダー内の新規または更新されたプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [@projectstream =] *projectstream*  
 バイナリ コンテンツ、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]プロジェクト配置ファイル (.ispac 拡張子) です。  
  
 ファイルのバイナリ コンテンツを取得するには、SELECT ステートメントと、OPENROWSET 関数および一括行セット プロバイダーを使用できます。 例については、次を参照してください。[展開 Integration Services (SSIS) プロジェクトとパッケージ](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)です。 OPENROWSET の詳細については、次を参照してください。 [OPENROWSET & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/openrowset-transact-sql.md).  
  
 *Projectstream*は**varbinary (max)**  
  
 [@operation_id =] *operation_id*  
 配置操作の一意識別子を返します。 *Operation_id*は**bigint**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   新しいプロジェクトを配置するフォルダーに対する CREATE_OBJECTS 権限、またはプロジェクトを更新するプロジェクトに対する MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 このストアド プロシージャがエラーを発生させる可能性がある条件を以下に示します。  
  
-   存在しないオブジェクトを参照するパラメーター、既に存在するオブジェクトを作成しようとするパラメーター、または何かの方法で無効になるパラメーター  
  
-   パラメーターの値 *@project_name* 展開ファイルで、プロジェクトの名前と一致しません  
  
-   ユーザーに十分な権限がない  
  
## <a name="remarks"></a>解説  
 プロジェクトの配置または更新中、ストアド プロシージャは、プロジェクトの個々のパッケージの保護レベルをチェックしません。  
  
  
