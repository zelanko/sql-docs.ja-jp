---
title: "catalog.get_parameter_values (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b1aeaf7-c938-4aef-bafc-e4d7a82eb578
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4ad8f0c367e38581db696d2aa32afd5b92d635d2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetparametervalues-ssisdb-database"></a>catalog.get_parameter_values (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  解決し、プロジェクトおよび対応するパッケージから既定のパラメーター値の取得、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```tsql  
get_parameter_values [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id  ]  
  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 パラメーターが存在するプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @package_name =] *package_name*  
 パッケージの名前です。 パッケージ名を指定して、すべてのプロジェクト パラメーターと指定されたパッケージのパラメーターを取得します。 NULL を使用すると、すべてのプロジェクト パラメーターとすべてのパッケージのパラメーターを取得します。 *Package_name*は**nvarchar (260)**です。  
  
 [ @reference_id =] *reference_id*  
 環境参照の一意の識別子。 このパラメーターはオプションです。 *Reference_id*は**bigint**です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 次の形式のテーブルを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|パラメーターの型。 値が`20`パラメーターと、値は、プロジェクトの`30`パッケージ パラメーターです。|  
|parameter_data_type|**nvarchar (128)**|パラメーターのデータ型です。|  
|parameter_name|**sysname**|パラメーターの名前。|  
|parameter_value|**sql_variant**|パラメーターの値。|  
|sensitive|**bit**|値が`1`パラメーター値はセンシティブです。 値が `0` の場合、パラメーター値はセンシティブではありません。|  
|required|**bit**|値が `1` の場合、実行を開始するためパラメーター値が必要です。 値が `0` の場合、実行を開始するためのパラメーター値は不要です。|  
|value_set|**bit**|値が`1`パラメーター値が割り当てられています。 値が`0`パラメーターの値が割り当てられていません。|  
  
> [!NOTE]  
>  リテラル値は、プレーン テキストで表示されます。 **NULL**が機微な値の代わりに表示されます。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトに対する読み取り権限と、該当する場合、参照先の環境に対する読み取りアクセス許可  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   指定したフォルダーまたはプロジェクトでパッケージが見つからない  
  
-   ユーザーに適切な権限がない  
  
-   指定した環境参照が存在しない  
  
  
