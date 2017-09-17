---
title: "catalog.set_worker_agent_property (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d0476bbb67cff44a05aed1441a31d679882b4cb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

プロパティを設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト ワーカーです。

## <a name="syntax"></a>構文

```tsql
set_worker_agent_property [ @WorkerAgentId = ] WorkerAgentId, [ @PropertyName = ] PropertyName, [ @PropertyValue = ] PropertyValue 
```

## <a name="arguments"></a>引数
[ @WorkerAgentId =] *WorkerAgentId*  
ワーカーのエージェントは、スケール アウト ワーカーの id。 *WorkerAgentId*は**uniqueidentifier**です。

[ @PropertyName =] *PropertyName*  
プロパティの名前。 *PropertyName*は**nvarchar (256)**です。

[ @PropertyValue =] *PropertyValue*  
プロパティの値。 *PropertyValue*は**nvarchar (max)**です。

## <a name="remarks"></a>解説
有効なプロパティの名前は**DisplayName**、**説明**、**タグ**です。

## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割

## <a name="erros-and-warnings"></a>エラーと警告
  エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   ユーザーに適切な権限がない 

-   ワーカー エージェント id が正しくありません。

-   プロパティ名が正しくありません。

-   プロパティ値は、vilid ではありません。  
