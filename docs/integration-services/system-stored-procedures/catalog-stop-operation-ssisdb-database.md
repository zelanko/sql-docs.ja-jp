---
title: catalog.stop_operation (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 97fd9d22-03dd-4eda-8f6c-ba8b67acec68
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 22f4a0a20039af5ea274d9b6c0fc00aa1f7b10f3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85674183"
---
# <a name="catalogstop_operation-ssisdb-database"></a>catalog.stop_operation (SSISDB データベース)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行の検証またはインスタンスを停止します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.stop_operation [ @operation_id = ] operation_id  
```  
  
## <a name="arguments"></a>引数  
 [ @operation_id = ] *operation_id*  
 実行の検証またはインスタンスの一意識別子。 *operation_id* は **bigint** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行の検証またはインスタンスの READ 権限および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   ユーザーに適切な権限がない  
  
-   操作の識別子が有効ではない  
  
-   操作が既に停止されている  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログで操作を停止できるのは、一度に 1 人のユーザーだけです。 複数のユーザーが操作を停止しようとすると、ストアド プロシージャは最初の試行で成功 (値 `0`) を返しますが、2 回目以降の試行ではエラーが発生します。  
  
  
