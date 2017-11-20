---
title: "catalog.set_object_parameter_value (SSISDB データベース) |Microsoft ドキュメント"
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
ms.assetid: fb887543-f92f-404d-9495-a1dd23a6716e
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3a5dc70b1e955b3c702dc9e9dbe4776cc4ebd5ac
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetobjectparametervalue-ssisdb-database"></a>catalog.set_object_parameter_value (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパラメーターの値を設定します。 環境変数に値を関連付けるか、またはその他の値が割り当てられていないときに既定で使用されるリテラル値を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_object_parameter_value [@object_type =] object_type   
    , [@folder_name =] folder_name   
    , [@project_name =] project_name   
    , [@parameter_name =] parameter _name   
    , [@parameter_value =] parameter_value   
 [  , [@object_name =] object_name ]  
 [  , [@value_type =] value_type ]  
```  
  
## <a name="arguments"></a>引数  
 [@object_type =] *object_type*  
 パラメーターの型。 値を使用して`20`プロジェクト パラメーターまたは値を示す`30`パッケージ パラメーターを示すためにします。 *Object_type*は**smallInt**です。  
  
 [@folder_name =] *folder_name*  
 パラメーターを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [@project_name =] *project_name*  
 パラメーターを含むプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [@parameter_name =] *parameter_name*  
 パラメーターの名前。 *Parameter_name*は**nvarchar (128)**です。  
  
 [@parameter_value =]*パラメーター*  
 パラメーターの値。 *パラメーター*は**sql_variant**です。  
  
 [@object_name =] *object_name*  
 パッケージの名前です。 パラメーターがパッケージ パラメーターである場合に必要な引数です。 *Object_name*は**nvarchar (260)**です。  
  
 [@value_type =] *value_type*  
 パラメーター値の型。 文字を使用して`V`ことを示す*パラメーター*実行前にその他の値が割り当てられていないときに既定で使用されるリテラル値です。 文字を使用して`R`ことを示す*パラメーター*参照されている値は、環境変数の名前に設定されています。 この引数は省略可能です。文字 `V` が既定で使用されます。 *Value_type*は**char (1)**です。  
  
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
 ストアド プロシージャがエラーを発生させる可能性がある条件を以下に示します。  
  
-   パラメーターの型が無効  
  
-   プロジェクト名が無効  
  
-   パッケージ パラメーターで、パッケージ名が無効  
  
-   値の型が無効  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>解説  
  
-   いない場合*value_type*が指定されているリテラル値*パラメーター*は既定で使用します。 リテラル値を使用すると、 *value_set*で、 [object_parameters](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)に設定されているビュー`1`です。 NULL パラメーター値は許可されません。  
  
-   場合*value_type*文字を含む`R`、参照先の値のことを示している*パラメーター*環境変数の名前を示します。  
  
-   値`20`に使用できる*object_type*プロジェクト パラメーターを示すためです。 この場合、値の*object_name*必要に応じて、かつ指定した値ではありません*object_name*は無視されます。 この値は、ユーザーがプロジェクトのパラメーターを設定するときに使用されます。  
  
-   値`30`に使用できる*object_type*パッケージ パラメーターを示すためです。 この場合、値の*object_name*は、対応するパッケージを表すために使用します。 場合*object_name*が指定されていない、ストアド プロシージャは、エラーが返され、終了します。  
  
  

