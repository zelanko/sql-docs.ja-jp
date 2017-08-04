---
title: "catalog.update_master_address (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e5e560d6011370b3d56ba13c86608d2be3d0dc6e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>catalog.update_master_address (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

更新プログラム、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト マスター エンドポイント。

## <a name="syntax"></a>構文

```tsql
update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>引数
[ @MasterAddress =] *masterAddress*  
スケール アウト マスター エンドポイントです。 *MasterAddress*は**nvarchar**です。  

 ## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>権限  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
   
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
 
