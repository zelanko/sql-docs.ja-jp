---
title: "catalog.validate_package (SSISDB データベース) |Microsoft ドキュメント"
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
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8b4dbd030c457bfb90ac4ec7fae886de28f96854
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパッケージを非同期的に検証します。  
  
## <a name="syntax"></a>構文  
  
```  
  
validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 パッケージを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 パッケージを含むプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @package_name =] *package_name*  
 パッケージの名前です。 *Package_name*は**nvarchar (260)**です。  
  
 [ @validation_id =] *validation_id*  
 検証の一意識別子 (ID) を返します。 *Validation_id*は**bigint**です。  
  
 [ @use32bitruntime =] *use32bitruntime*  
 64 ビット オペレーティング システムでパッケージを実行する 32 ビット ランタイムを使用するかどうかを示します。 値を使用して`1`64 ビット オペレーティング システムで実行されているときに、32 ビット ランタイムを使用してパッケージを実行します。 値 `0` を使用すると、64 ビット オペレーティング システムで実行しているときに、64 ビット ランタイムでパッケージが実行されます。 このパラメーターはオプションです。 *Use32bitruntime*は**ビット**です。  
  
 [ @environment_scope =] *environment_scope*  
 検証が考慮する環境参照を示します。 値が `A` の場合は、プロジェクトに関連するすべての環境参照が検証に含まれます。 値が `S` の場合は、1 つの環境参照のみが含まれます。 値が`D`、環境参照は含まれず、各パラメーターでは、検証に合格するために既定のリテラル値があります。 このパラメーターは省略可能です。文字 `D` が既定で使用されます。 *Environment_scope*は**char (1)**です。  
  
 [ @reference_id =] *reference_id*  
 環境参照の一意の ID。 検証で、1 つの環境参照が含まれている場合にのみ、このパラメーターは必要なときに*environment_scope*は`S`します。 *Reference_id*は**bigint**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ 権限と、該当する場合は、参照先の環境での READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   プロジェクト名またはパッケージ名が無効  
  
-   ユーザーに適切な権限がない  
  
-   検証に含まれる 1 つまたは複数の参照先の環境が、参照先の変数を含まない  
  
-   パッケージの検証に失敗する  
  
-   参照先の環境が存在しない  
  
-   参照先の変数が、検証に含まれる参照先の環境で見つからない  
  
-   変数がパッケージ パラメーターで参照されるが、参照先の環境が検証に含まれなかった  
  
## <a name="remarks"></a>解説  
 検証では、パッケージが正常に実行されない問題を特定することができます。 使用して、 [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md)または[catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md)検証の状態を監視するビュー。  
  
  
