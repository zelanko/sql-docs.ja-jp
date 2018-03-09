---
title: "catalog.get_parameter_values (SSISDB データベース) | Microsoft Docs"
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
ms.assetid: 5b1aeaf7-c938-4aef-bafc-e4d7a82eb578
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7fcb3ffcdd35f2b526f1e84ce36c206919e8eb74
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="cataloggetparametervalues-ssisdb-database"></a>catalog.get_parameter_values (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのプロジェクトおよび対応するパッケージの既定のパラメーター値を解決し、取得します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.get_parameter_values [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id  ]  
  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name = ] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *folder_name* は **nvarchar(128)** です。  
  
 [ @project_name = ] *project_name*  
 パラメーターが存在するプロジェクトの名前。 *project_name* は **nvarchar(128)** です。  
  
 [ @package_name = ] *package_name*  
 パッケージの名前です。 パッケージ名を指定して、すべてのプロジェクト パラメーターと指定されたパッケージのパラメーターを取得します。 NULL を使用すると、すべてのプロジェクト パラメーターとすべてのパッケージのパラメーターを取得します。 *package_name* は **nvarchar (260)** です。  
  
 [ @reference_id = ] *reference_id*  
 環境参照の一意識別子。 このパラメーターはオプションです。 *reference_id* は **bigint** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 次の形式のテーブルを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|パラメーターの型。 プロジェクト パラメーターでは値は `20`、パッケージ パラメーターでは値は `30` です。|  
|parameter_data_type|**nvarchar(128)**|パラメーターのデータ型です。|  
|parameter_name|**sysname**|パラメーターの名前。|  
|parameter_value|**sql_variant**|パラメーターの値。|  
|sensitive|**bit**|値が `1` の場合、パラメーター値はセンシティブです。 値が `0` の場合、パラメーター値はセンシティブではありません。|  
|required|**bit**|値が `1` の場合、実行を開始するためパラメーター値が必要です。 値が `0` の場合、実行を開始するためのパラメーター値は不要です。|  
|value_set|**bit**|値が `1` の場合、パラメーター値は割り当てられています。 値が `0` の場合、パラメーター値は割り当てられていません。|  
  
> [!NOTE]  
>  リテラル値は、プレーン テキストで表示されます。 センシティブ値の場合は、代わりに **NULL** が表示されます。  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ アクセス許可と、該当する場合は、参照先の環境での READ アクセス許可  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   指定したフォルダーまたはプロジェクトでパッケージが見つからない  
  
-   ユーザーに適切な権限がない  
  
-   指定した環境参照が存在しない  
  
  
