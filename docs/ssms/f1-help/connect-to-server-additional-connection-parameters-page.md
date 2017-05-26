---
title: "[サーバーへの接続] ([追加の接続パラメーター] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7befc61bcf4a973aa0593e476bcce76f5751f40b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-additional-connection-parameters-page"></a>[サーバーへの接続] \([追加の接続パラメーター] ページ)
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] の **[接続先]** ダイアログ ボックスには、オプションとして最も一般的な接続文字列値が表示されます。 **[追加の接続パラメーター]** ページを使用すると、接続文字列に接続パラメーターをさらに追加できます。  
  
-   追加の接続パラメーターには、任意の ODBC 接続パラメーターを使用できます。  
  
-   追加の接続パラメーターは、 **;parameter1=value1;parameter2=value2**という形式で追加する必要があります。  
  
-   **[追加の接続パラメーター]** ページを使用して追加したパラメーターは、 **[接続先]** ダイアログ ボックスのオプションを使用して選択したパラメーターに追加されます。  
  
-   指定した各パラメーターの最後のインスタンスは、そのパラメーターの前のインスタンスよりも優先されます。 **[追加の接続パラメーター]** ページを使用して追加したパラメーターは、 **[ログイン]** タブまたは **[接続プロパティ]** タブで指定したパラメーターより優先されます。 たとえば、 **[ログイン]** タブの **[サーバー名]** で「 **SERVER1**」と指定し、 **[追加の接続パラメーター]** ページで「 **;SERVER=SERVER2**」と指定した場合、 **SERVER2**に接続されます。  
  
-   **[追加の接続パラメーター]** ページで追加したパラメーターは、常にプレーン テキストとして渡されます。  
  
    > [!IMPORTANT]  
    > **[追加の接続パラメーター]** ページにはログイン資格情報やパスワードを含めないでください。 このダイアログ ボックスで指定したパラメーターは、ネットワーク経由で渡されるときに暗号化されません。 代わりに **[ログイン]** タブを使用してください。  
  
## <a name="task-list"></a>タスク一覧  
  
### <a name="to-show-the-additional-connection-parameters-page"></a>[追加の接続パラメーター] ページを表示するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)]で、 **[クエリ]** メニューの **[接続]**をポイントし、 **[接続]**をクリックします。  
  
2.  **[接続先]** ダイアログ ボックスで、 **[オプション]**をクリックし、 **[追加の接続パラメーター]** タブをクリックします。  
  
## <a name="examples"></a>使用例  
  
### <a name="example-a-connecting-to-the-database-engine"></a>例 A: データベース エンジンへの接続  
ACCOUNTING というサーバーの [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] データベースに接続するには、 **[追加の接続パラメーター]** ページに次のように入力します。  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a>例 B: Analysis Services への接続  
分析サーバーに接続し、通知をリッスンするすべてのパーティションに対するクエリが (キャッシュをバイパスして) リアルタイムで実行されるようにして、書き戻しのタイムアウト値を 5 に設定するには、 **[追加の接続パラメーター]** ページに次のように入力します。  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  

