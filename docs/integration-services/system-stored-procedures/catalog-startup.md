---
title: catalog.startup |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0d2a407f0e45459dfeefa6265aceedce24e365a7
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
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
  
  
