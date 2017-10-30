---
title: "catalog.set_execution_property_override_value |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20f2c882a78f5e60931b0152d5877898e1972d0a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetexecutionpropertyoverridevalue"></a>catalog.set_execution_property_override_value
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行のインスタンスにプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id =] *execution_id*  
 実行のインスタンスの一意の識別子。 *Execution_id*は**bigint**です。  
  
 [ @property_path =] *property_path*  
 パッケージ内のプロパティのパス。 *Property_path*は**nvarchar (4000)**です。  
  
 [ @property_value =] *property_value*  
 プロパティに割り当てるオーバーライド値。 *Property_value*は**nvarchar (max)**です。  
  
 [ @sensitive =]*機密性の高い*  
 値が 1 のとき、プロパティはセンシティブで、格納されるときに暗号化されます。 値が 0 のとき、プロパティはセンシティブではなく、値はプレーンテキストで格納されます。 *機密性の高い*引数は**ビット**です。  
  
## <a name="remarks"></a>解説  
 この手順と同じ機能を実行、**プロパティのオーバーライド**」の「、 **[詳細設定]**のタブ、**パッケージ実行**ダイアログ。 プロパティへのパスがから派生した、**パッケージ パス**パッケージ タスクのプロパティです。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   ユーザーに適切な権限がない  
  
-   実行識別子が有効ではない  
  
-   プロパティ パスが無効  
  
-   プロパティ値のデータ型が、プロパティのデータ型と一致しない  
  
## <a name="see-also"></a>参照  
 [catalog.set_execution_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  

