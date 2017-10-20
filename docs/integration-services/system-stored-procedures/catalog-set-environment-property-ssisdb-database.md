---
title: "catalog.set_environment_property (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8eedfe6919a69759cc6de3645b3e1f965dcdd0c6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentproperty-ssisdb-database"></a>catalog.set_environment_property (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  環境のプロパティを設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 環境を含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @environment_name =] *environment_name*  
 環境の名前。 *Environment_name*は**nvarchar (128)**です。  
  
 [ @property_name =] *property_name*  
 環境プロパティの名前。 *Property_name*は**nvarchar (128)**です。  
  
 [ @property_value =] *property_value*  
 環境プロパティの値。 *Property_value*は**nvarchar (1024)**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   環境の READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   フォルダー名が無効  
  
-   プロパティ名が無効  
  
-   環境名が無効  
  
## <a name="remarks"></a>解説  
 このリリースで設定できるのは `Description` プロパティだけです。 `Description` プロパティのプロパティ値は 4,000 文字を超えることはできません。  
  
  
