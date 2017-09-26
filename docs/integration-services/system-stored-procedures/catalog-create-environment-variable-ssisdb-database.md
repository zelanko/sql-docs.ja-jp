---
title: "catalog.create_environment_variable (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91ed017b-6567-4bf2-b9f1-e2b5c70a5343
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 62aa7f67d7c7b33ac61d63b10fe45d604029500b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentvariable-ssisdb-database"></a>catalog.create_environment_variable (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  環境変数を作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```tsql  
create_environment_variable [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
    , [ @data_type = ] data_type  
    , [ @sensitive = ] sensitive  
    , [ @value = ] value  
    , [ @description = ] description  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 環境を含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @environment_name =] *environment_name*  
 環境の名前。 *Environment_name*は**nvarchar (128)**です。  
  
 [ @variable_name =] *variable_name*  
 環境変数の名前。 *Variable_name*は**nvarchar (128)**です。  
  
 [ @data_type =] *data_type*  
 変数のデータ型。 環境変数のデータ型はサポートされている**ブール**、**バイト**、 **DateTime**、**二重**、 **Int16**、 **Int32**、 **Int64**、**単一**、**文字列**、 **UInt32**、および**UInt64**です。 サポートされていない環境変数のデータ型は**Char**、 **DBNull**、**オブジェクト**、および**Sbyte**です。 データ型、 *data_type*パラメーターは**nvarchar (128)**です。  
  
 [ @sensitive =]*機密性の高い*  
 変数がセンシティブ値を含むかどうかを示します。 値を使用して`1`環境変数の値を区別するかの値であることを示す`0`されていないことを示すためにします。 センシティブ値が格納される場合、その値は暗号化されます。 機密性の高いではない値は、プレーン テキストで格納されます。*機密性の高い*は**ビット**です。  
  
 [ @value =]*値*  
 環境変数の値。 *値*は**sql_variant**です。  
  
 [ @description =]*の説明*  
 環境変数の説明。 *値*は**nvarchar (1024)**です。  
  
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
  
-   フォルダー名、環境名、または環境変数名が無効  
  
-   変数名が環境に既に存在する  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>解説  
 パッケージの実行で使用するため、値をプロジェクト パラメーターまたはパッケージ パラメーターに効率的に割り当てるには、環境変数を使用できます。 環境変数は、パラメーター値を編成できるようにします。 変数名は、環境内で一意である必要があります。  
  
 ストアド プロシージャは変数のデータ型を検証して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログでサポートされることを確認します。  
  
> [!TIP]  
>  使用を検討して、 **Int16**のデータ型の[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ではなく、サポートされていない**Sbyte**データ型。  
  
 このストアド プロシージャに渡される値、*値*パラメーターから変換されます、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のデータ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次の表に従って、データ型。  
  
|Integration Services データ型|SQL Server データ型|  
|------------------------------------|--------------------------|  
|**ブール値**|**bit**|  
|**バイト**|**バイナリ**、 **varbinary**|  
|**DateTime**|**datetime**、 **datetime2**、 **datetimeoffset**、 **smalldatetime**|  
|**Double**|正確な numeric: **decimal**、**数値**です。おおよその numeric: **float**、 **real**|  
|**Int16 型**|**smallint**|  
|**Int32**|**int**|  
|**Int64**|**bigint**|  
|**単一**|正確な numeric: **decimal**、**数値**です。おおよその numeric: **float**、 **real**|  
|**文字列**|**varchar**、 **nvarchar**、 **char**|  
|**UInt32**|**int** (これは、使用可能なマッピングに最も近い**Uint32**)。|  
|**UInt64**|**bigint** (これは、使用可能なマッピングに最も近い**Uint64**)。|  
  
  
