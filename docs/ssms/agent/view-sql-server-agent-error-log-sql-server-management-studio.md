---
title: "SQL Server エージェントのエラー ログの表示 (SQL Server Management Studio) | Microsoft Docs"
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
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 31fbf087c088a0f83471a37b60d5151b9db315b3
ms.lasthandoff: 04/11/2017

---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a>SQL Server エージェントのエラー ログの表示 (SQL Server Management Studio)
このトピックでは、  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]エージェントのエラー ログを表示する方法について説明します。  
  
[ログ ファイルの表示] には、さまざまなコンポーネントのログ情報が表示されます。 [ログ ファイルの表示] が開いているときに **[ログの選択]** ペインを使用して、表示するログを選択します。 各ログには、そのログの種類に適した列が表示されます。 表示できるログ ファイルは、[ログ ファイルの表示] を開いたときの状況に応じて変わります。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントのエラー ログを表示するには](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-view-the-includessnoversionincludesssnoversionmdmd-agent-error-log"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのエラー ログを表示するには  
  
1.  **オブジェクト エクスプローラー**で、表示する [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  プラス記号をクリックして **[エラー ログ]** フォルダーを展開します。  
  
4.  表示するエラー ログを右クリックし、 **[エージェント ログの表示]**を選択します。  
  
    **server_name**** ダイアログ ボックスでは、次のオプションを使用できます。  
  
    **[ログの読み込み]**  
    読み込むログ ファイルを指定できるダイアログ ボックスが開きます。  
  
    **[エクスポート]**  
    **[ログ ファイルの概要]** グリッドに表示されている情報をテキスト ファイルとしてエクスポートするためのダイアログ ボックスが開きます。  
  
    **[更新]**  
    選択されたログの表示を更新します。 **[更新]** ボタンをクリックすると、選択したログが対象サーバーから再度読み込まれ、それと同時にすべてのフィルター設定が適用されます。  
  
    **[フィルター]**  
    **[接続]**や **[日付]**などの **[全般]** フィルター基準を含め、ログ ファイルのフィルター選択に使用する設定を指定できるダイアログ ボックスが開きます。  
  
    **検索**  
    ログ ファイル内で特定のテキストを検索します。 ワイルドカード文字を使用した検索はサポートされません。  
  
    **[停止]**  
    ログ ファイル エントリの読み込みを停止します。 たとえば、最新のエントリのみを表示したい場合に、リモートまたはオフラインのログ ファイルの読み込みに長い時間がかかるときは、このオプションを使用することをお勧めします。  
  
    **[ログ ファイルの概要]**  
    この情報パネルには、ログ ファイルのフィルター選択の概要が表示されます。 ファイルがフィルター選択されない場合、 **"フィルターが適用されていません"**と表示されます。 ログにフィルターが適用されている場合、" **ログ エントリのフィルター条件:** <filter criteria>" と表示されます。  
  
    **[選択した行の詳細]**  
    行を選択すると、選択されたイベント行の詳細情報がページの下部に表示されます。 列をグリッド内の別の場所にドラッグすることで、列を並べ替えることができます。 グリッドのヘッダーで列のセパレーター バーを左右にドラッグすると、列の幅を変更できます。 グリッドのヘッダーで列のセパレーター バーをダブルクリックすると、内容の長さに合わせて自動的に列の幅が調整されます。  
  
    **インスタンス**  
    イベントが発生したインスタンスの名前です。 これは、 *computer name*\\*instance name*と表示されます。  
  
    **[日付]**  
    イベントの日付が表示されます。  
  
    **ソース**  
    サービスの名前 (たとえば MSSQLSERVER) など、イベントの作成元のソース機能が表示されます。 ログの種類によっては表示されません。  
  
    **メッセージ**  
    イベントに関連付けられているメッセージがすべて表示されます。  
  
    **[ログの種類]**  
    イベントが属するログの種類が表示されます。 [ログ ファイルの概要] ウィンドウには、選択したログがすべて表示されます。  
  
    **[ログ ソース]**  
    イベントがキャプチャされているソース ログの説明が表示されます。  
  
5.  完了したら、 **[閉じる]**をクリックします。  
  

