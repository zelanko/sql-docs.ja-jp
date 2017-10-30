---
title: "catalog.configure_catalog (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 15bec231bf1de825cea952e07827074d56751386
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogconfigurecatalog-ssisdb-database"></a>catalog.configure_catalog (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  カタログ プロパティを特定の値に設定することによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログを構成します。  
  
## <a name="syntax"></a>構文  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>引数  
 [ @property_name =] *property_name*  
 カタログ プロパティの名前。 *Property_name*は**nvarchar (255)**です。 使用可能なプロパティの詳細については、次を参照してください。 [catalog.catalog_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value =] *property_value*  
 カタログ プロパティの値。 *Property_value*は**nvarchar (255)**です。 プロパティ値の詳細については、次を参照してください。 [catalog.catalog_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャを指定するかどうか、 *property_value*ごとに有効なは*property_name*です。  
  
 このストアド プロシージャは、実行が保留中、キュー状態、実行中、一時停止中など、アクティブな実行がない場合にのみ実行できます  
  
 カタログが構成されているときにその他のすべてのカタログ ストアド プロシージャの失敗、エラー メッセージ「サーバーは現在構成されています」
  
 カタログが構成されている場合は、エントリが操作ログに書き込まれます。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   プロパティが存在しない  
  
-   プロパティ値が無効  
  
  

