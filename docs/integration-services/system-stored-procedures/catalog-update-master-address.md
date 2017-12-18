---
title: "catalog.update_master_address (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b45f8499914ecd87a7073a5373377b85dc8a77f4
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>catalog.update_master_address (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master エンドポイントを更新します。

## <a name="syntax"></a>構文

```sql
catalog.update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>引数
[ @MasterAddress = ] *masterAddress*  
Scale Out Master エンドポイント。 *masterAddress* は **nvarchar** です。  

 ## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
   
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
 
