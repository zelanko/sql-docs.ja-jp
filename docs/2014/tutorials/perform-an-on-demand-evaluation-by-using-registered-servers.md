---
title: 登録済みサーバーを使用して要求時評価を実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e3ffcef923eaeb3ba48eacaca870bd3355fb6661
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85035578"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>登録済みサーバーを使用した要求時評価の実行

  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して登録済みサーバーを使用して、ベスト プラクティス ポリシーの要求時評価を実行できます。 使用できるのは、ローカル サーバー グループまたは中央管理サーバーのいずれかです。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 以降のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているサーバー グループ メンバーに対して、ベスト プラクティス ポリシーの要求時評価を実行できます。 ただし、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] または [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] でサポートされていない一部のプロパティがポリシーによって参照される場合は、例外エラーが発生することがあります。  
  
## <a name="prerequisites"></a>前提条件  
 この作業を実行するには、登録済みサーバーでサーバー登録を 1 つ以上構成しておく必要があります。 詳細については、次のトピックを参照してください。  
  
-   [サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [接続されたサーバー &#40;SQL Server Management Studio&#41;に登録](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)します。  
  
-   [中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>サーバー グループに対してベスト プラクティス ポリシーを評価するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。  
  
2.  構成に応じて [**データベースエンジン**] を展開し、[**ローカルサーバーグループ**] または [**中央管理サーバー**] を展開します。  
  
3.  次のいずれかの操作を行います。  
  
    -   ローカルサーバーグループまたは中央管理サーバーで管理されているすべてのサーバーに対してポリシーを評価するには、ローカルサーバーグループ名または中央管理サーバー名を右クリックし、[**ポリシーの評価**] をクリックします。  
  
        > [!NOTE]  
        >  中央管理サーバーを通じてポリシーを評価する場合、ポリシーは中央管理サーバー自体に対しては評価されません。  
  
    -   特定のサーバーまたはサーバーグループに対してポリシーを評価するには、[**ローカルサーバーグループ**] または [中央管理サーバー名] を展開し、ポリシーを評価するサーバーまたはサーバーグループを右クリックして、[**ポリシーの評価**] をクリックします。  
  
4.  [**ポリシーの評価**] ダイアログボックスの [**ソース**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。  
  
5.  [**ソースの選択**] ダイアログボックスで、評価するポリシーファイルのソースとして [**ファイル**] または [**サーバー** ] を選択できます。 [**サーバー**] をクリックすると、以前にローカルサーバーまたはリモートサーバー上のポリシーベースの管理にインポートされたベストプラクティスポリシーの要求時評価を実行できます。 このチュートリアルでは、[**ファイル**] をクリックし、評価する個々のポリシーファイルを選択します。 そのためには、次の手順に従います。  
  
    1.  [**ファイル**] をクリックします。  
  
    2.  [**ファイル**] の横にある省略記号ボタン ([.**..**]) をクリックします。  
  
    3.  評価する1つまたは複数の .xml ポリシーファイルを選択し、[**開く**] をクリックします。  
  
         選択したファイルの一覧が [**ファイル**] ボックスに表示されます。  
  
    4.  [**ソースの選択**] ダイアログボックスで、[ **OK**] をクリックします。  
  
    5.  [**ポリシーの読み込み**] ダイアログボックスが表示されたら、[**閉じる**] をクリックします。  
  
     選択したポリシーは、[ポリシーの**選択**] ページに一覧表示されます。 ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。  
  
6.  [**評価**] をクリックしてポリシーを評価します。  
  
7.  一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。 このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。 チェックボックスをオンにした場合、または失敗したポリシーが含まれている行をクリックすると、評価に失敗したターゲットインスタンスの横にある [**対象の詳細**] ペインにチェックボックスが表示されます。 いずれかのチェックボックスをオンにすると、[**適用**] ボタンが使用できるようになります。 [**適用**] をクリックすると、選択したターゲットインスタンスの準拠していない設定が自動的に更新されます。  
  
    > [!CAUTION]  
    >  ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。 1つ以上のチェックボックスをオンにした後、[**スクリプト**] をクリックし、出力場所を選択して、変更を適用する前に基になるコードを確認できるようにすることをお勧めし [!INCLUDE[tsql](../includes/tsql-md.md)] ます。  
  
8.  ポリシーの詳細な結果を表示するには、[**結果**] テーブルでポリシーをクリックします。 [**対象の詳細**テーブルには、各インスタンスの詳細が表示されます。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベストプラクティスの監視と実施](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [中央管理サーバーを使用した複数のサーバーの管理](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
