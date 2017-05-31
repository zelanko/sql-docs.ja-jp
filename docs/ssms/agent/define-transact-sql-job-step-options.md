---
title: "Transact-SQL ジョブ ステップのオプションを定義する | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4bf48de41b0d89e7b2edc063010bf20826463b22
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="define-transact-sql-job-step-options"></a>Define Transact-SQL Job Step Options
このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql_md.md)]  [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] エージェントの [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ジョブ ステップのオプションを定義する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **Transact-SQL ジョブ ステップのオプションを定義する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-define-transact-sql-job-step-options"></a>Transact-SQL ジョブ ステップのオプションを定義するには  
  
1.  **オブジェクト エクスプローラー**で、 **[SQL Server エージェント]**を展開し、 **[ジョブ]**を展開します。次に、編集するジョブを右クリックし、 **[プロパティ]**をクリックします。  
  
2.  **[ステップ]** ページをクリックし、ジョブ ステップをクリックして、 **[編集]**をクリックします。  
  
3.  **[ジョブ ステップのプロパティ]** ダイアログ ボックスで、ジョブの種類が **[Transact-SQL スクリプト (T-SQL)]**であることを確認し、 **[詳細設定]** ページを選択します。  
  
4.  **[成功した場合のアクション]** ボックスで、ジョブが成功した場合に実行するアクションを指定します。  
  
5.  **[再試行回数]** ボックスに 0 ～ 9999 の数値を入力して、再試行回数を指定します。  
  
6.  **[再試行間隔]** ボックスに 0 ～ 9999 の数 (分) を入力して、再試行間隔を指定します。  
  
7.  **[失敗した場合のアクション]** ボックスで、ジョブが失敗した場合に実行するアクションを指定します。  
  
8.  ジョブが [!INCLUDE[tsql](../../includes/tsql_md.md)] スクリプトの場合は、以下の方法から選択できます。  
  
    -   **[出力ファイル]**ボックスに、出力ファイルの名前を入力します。 既定では、ジョブ ステップの実行ごとに出力ファイルが上書きされます。 出力ファイルを上書きしない場合は、 **[既存のファイルに出力を追加する]**チェック ボックスをオンにします。 このオプションは、 **sysadmin** 固定サーバー ロールのメンバーだけが使用できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] では、ユーザーはファイル システム上の任意のファイルを表示できないので、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] を使用して、ファイル システムに書き込まれたジョブ ステップのログを表示できないことに注意してください。  
  
    -   ジョブ ステップのログをデータベース テーブルに記録する場合は、 **[テーブルにログ記録する]** チェック ボックスをオンにします。 既定では、ジョブ ステップの実行ごとにテーブルの内容が上書きされます。 テーブルの内容を上書きしない場合は、 **[テーブル内の既存のエントリに出力を追加する]**チェック ボックスをオンにします。 ジョブ ステップの実行後にこのテーブルのコンテンツを表示するには、 **[表示]**をクリックします。  
  
    -   ステップの履歴に出力を含める場合は、 **[履歴にステップ出力を含める]** チェック ボックスをオンにします。 エラーがない場合にのみ、出力は表示されます。 また、出力が切り捨てられる場合があります。  
  
9. **sysadmin** 固定サーバー ロールのメンバーで、このジョブ ステップを別の SQL ログインで実行する場合は、 **[実行時のユーザー]** ボックスで SQL ログインを選択します。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**Transact-SQL ジョブ ステップのオプションを定義するには**  
  
Visual Basic、Visual C#、PowerShell などの選択したプログラミング言語で **JobStep** クラスを使用します。  
  

