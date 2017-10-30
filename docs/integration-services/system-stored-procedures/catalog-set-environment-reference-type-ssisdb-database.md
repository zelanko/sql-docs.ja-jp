---
title: "catalog.set_environment_reference_type (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b79e3a06-22c0-40e5-8933-1b3414db3329
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e83d9979ee4736528efb4851848ea3eac717fab8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentreferencetype-ssisdb-database"></a>catalog.set_environment_reference_type (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  プロジェクトの既存の環境参照に関連付けられている参照の種類と環境名の設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_environment_reference_location [ @reference_id = reference_id  
    , [ @reference_type = ] reference_type  
 [  , [ @environment_folder_name = ] environment_folder_name ]  
```  
  
## <a name="arguments"></a>引数  
 [ @reference_id =] *reference_id*  
 更新される環境参照の一意識別子。 *Reference_id*は**bigint**です。  
  
 [ @reference_type =] *reference_type*  
 環境をプロジェクトと同じフォルダーに配置できるか (相対参照)、または別のフォルダーに配置できるか (絶対参照) を示します。 相対参照を指定するには、値 `R` を使用します。 絶対参照を指定するには、値 `A` を使用します。 *Reference_type*は**char (1)**です。  
  
 [ @environment_folder_name =] *environment_folder_name*  
 環境が配置されているフォルダー。 この値は絶対参照にする必要があります。 *Environment_folder_name*は**nvarchar (128)**です。  
  
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
  
-   フォルダー名、環境名、または参照 ID が有効ではない  
  
-   ユーザーが不適切なアクセス許可  
  
-   使用して絶対参照が指定されて、`A`文字内、 *reference_location*パラメーターは、フォルダーの名前がで指定されていない、 *environment_folder_name*パラメーター。  
  
## <a name="remarks"></a>解説  
 プロジェクトでは、相対または絶対環境参照を使用できます。 相対参照では、環境を名前で参照され、プロジェクトと同じフォルダーに格納されている必要があります。 絶対参照の場合、名前とフォルダーによって環境を参照します。プロジェクトとは異なるフォルダーに格納されている環境を参照する場合があります。 プロジェクトでは複数の環境を参照できます。  
  
> [!IMPORTANT]  
>  相対参照が指定されている場合、 *environment_folder_name*パラメーターの値を使用しないと、環境フォルダー名が自動的に設定**NULL**です。 環境フォルダー名を指定する必要があります絶対参照が指定されている場合、 *environment_folder_name*パラメーター。  
  
  

