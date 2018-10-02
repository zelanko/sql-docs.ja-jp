---
title: catalog.set_worker_agent_property (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cced4127afe6e32a536403f4e5c8fdfc0b758dfd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827080"
---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker のプロパティを設定します。

## <a name="syntax"></a>構文

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>引数
[@WorkerAgentId =] *WorkerAgentId*  
Scale Out Worker の worker エージェント ID。 *WorkerAgentId* は **uniqueidentifier** です。

[@PropertyName =] *PropertyName*  
プロパティの名前。 *PropertyName* は **nvarchar(256)** です。

[@PropertyValue =] *PropertyValue*  
プロパティの値です。 *PropertyValue* は **nvarchar(max)** です。

## <a name="remarks"></a>Remarks
有効なプロパティ名は、**DisplayName**、**Description**、**Tags** です。

## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ

## <a name="errors-and-warnings"></a>エラーおよび警告
  エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   ユーザーに適切な権限がない 

-   worker エージェント ID が正しくない

-   プロパティ名が無効

-   プロパティ値が無効  
