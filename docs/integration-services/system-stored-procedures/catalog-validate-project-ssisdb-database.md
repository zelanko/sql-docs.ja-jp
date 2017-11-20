---
title: "catalog.validate_project (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 5270689a-46d4-4847-b41f-3bed1899e955
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 83439015694f4235af4a67e994e916651ec63cc1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidateproject-ssisdb-database"></a>catalog.validate_project (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  プロジェクトを非同期的に検証、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="syntax"></a>構文  
  
```sql
catalog.validate_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @validate_type = ] validate_type  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>引数  
 [ @folder_name =] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [ @project_name =] *project_name*  
 プロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [ @validate_type =] *validate_type*  
 実行する検証の種類を示します。 文字 `F` を使用すると、完全な検証を実行します。 *Validate_type*は**char (1)**です。  
  
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
 検証手順の出力は、結果セットの異なるセクションとして返されます。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ 権限と、該当する場合は、参照先の環境での READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を次に示します。  
  
-   プロジェクト内の 1 つまたは複数のパッケージの検証の失敗  
  
-   検証に含まれる 1 つまたは複数の参照先の環境が、参照先の変数を含まない場合の検証の失敗  
  
-   指定した検証の種類が無効  
  
-   プロジェクト名または環境参照の ID が無効  
  
-   ユーザーに適切な権限がない  
  
## <a name="remarks"></a>解説  
 検証では、プロジェクトのパッケージが正常に実行されない問題を特定することができます。 使用して、 [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md)または[catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md)検証の状態を監視するビュー。  
  
 検証で使用できるのは、ユーザーがアクセスできる環境のみです。 検証の出力は結果セットとしてクライアントに送信されます。  
  
 このリリースでは、プロジェクトの検証は、依存関係の検証をサポートしていません。  
  
 完全な検証では、すべての参照先の環境変数が、検証に含まれていたすべての参照先の環境内で見つかることを確認します。 完全な検証結果では、検証に含まれていた参照先の環境で見つからなかった、有効な参照先の環境変数ではない環境参照を一覧表示します。  
  
  

