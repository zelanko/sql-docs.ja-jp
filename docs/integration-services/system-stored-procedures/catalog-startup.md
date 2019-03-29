---
title: catalog.startup |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ecf3e743fc0f5f4a9af213e97fc7adbf6ce1fe8c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271038"
---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SSISDB カタログに対する操作の状態のメンテナンスを実行します。  
  
 このストアド プロシージャは、[!INCLUDE[ssIS](../../includes/ssis-md.md)] サーバー インスタンスがダウンした場合に、実行されていたパッケージの状態を修正します。  
  
 **[カタログの作成]** ダイアログ ボックスの **[Enable automatic execution of Integration Services stored procedure at SQL Server startup]\(SQL Server の起動時に Integration Services ストアド プロシージャの自動実行を有効にする\)** オプションを選択すると、[!INCLUDE[ssIS](../../includes/ssis-md.md)] インスタンスが再起動されるたびに、ストアド プロシージャが自動実行されるようにできます。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ および MODIFY 権限、プロジェクトの READ および EXECUTE 権限、参照先の環境の READ 権限 (該当する場合)。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
  
