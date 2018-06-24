---
title: 登録済みサーバーを使用して時評価を実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f7deecbab3fceb117bfb3d237cf5940fdc34f5bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071808"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a>登録済みサーバーを使用した要求時評価の実行
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して登録済みサーバーを使用して、ベスト プラクティス ポリシーの要求時評価を実行できます。 使用できるのは、ローカル サーバー グループまたは中央管理サーバーのいずれかです。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 以降のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているサーバー グループ メンバーに対して、ベスト プラクティス ポリシーの要求時評価を実行できます。 ただし、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] または [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] でサポートされていない一部のプロパティがポリシーによって参照される場合は、例外エラーが発生することがあります。  
  
## <a name="prerequisites"></a>前提条件  
 この作業を実行するには、登録済みサーバーでサーバー登録を 1 つ以上構成しておく必要があります。 詳細については、次の各トピックを参照してください。  
  
-   [サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [接続のサーバーの登録&#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)です。  
  
-   [中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a>サーバー グループに対してベスト プラクティス ポリシーを評価するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[登録済みサーバー]** をクリックします。  
  
2.  展開**データベース エンジン**、いずれかを展開**ローカル サーバー グループ**、または**中央管理サーバー**構成に応じて、します。  
  
3.  以下のいずれかを実行します。  
  
    -   ローカル サーバー グループによって管理されているすべてのサーバーまたは中央管理サーバーに対して、ポリシーを評価するため、ローカル サーバー グループ名または中央管理サーバー名を右クリックし、をクリックして**ポリシーの評価**.  
  
        > [!NOTE]  
        >  中央管理サーバーを通じてポリシーを評価する場合、ポリシーは中央管理サーバー自体に対しては評価されません。  
  
    -   特定のサーバーまたはサーバー グループに対してポリシーを評価する展開**ローカル サーバー グループ**または名前をサーバーまたはに対して、ポリシーを評価し、をクリックするサーバー グループを右クリックし、中央管理サーバー**ポリシーの評価**です。  
  
4.  **ポリシーの評価** ダイアログ ボックスで、**ソース**ボックスで、省略記号ボタン (**.**) ボタンをクリックします。  
  
5.  **ソースの選択** ダイアログ ボックスを選択できます。**ファイル**または**サーバー**を評価するポリシー ファイルのソースとして。 クリックすると**サーバー**、ローカルまたはリモート サーバー上のポリシー ベースの管理に以前インポートされたすべてのベスト プラクティス ポリシーのオンデマンドで評価を行うことができます。 このチュートリアルをクリックして**ファイル**、し評価する個々 のポリシー ファイルを選択します。 これを行うには、次の手順を実行します。  
  
    1.  をクリックして**ファイル**です。  
  
    2.  横に**ファイル**、省略記号ボタン (**.**) ボタンをクリックします。  
  
    3.  評価、およびをクリックする 1 つまたは複数の .xml ポリシー ファイルを選択**開く**です。  
  
         選択したファイルの一覧に表示されます、**ファイル**ボックス。  
  
    4.  **ソースの選択**ダイアログ ボックスで、をクリックして**OK**です。  
  
    5.  場合、**ポリシーを読み込んでいます** ダイアログ ボックスが表示されたら、をクリックして**閉じる**です。  
  
     選択したポリシーは次の一覧に表示されます、**ポリシーの選択**ページ。 ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。  
  
6.  をクリックして**評価**ポリシーを評価します。  
  
7.  一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。 このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。 チェック ボックスが表示される場合は、チェック ボックスを選択するか、失敗したポリシーを含む行をクリックすると、**対象の詳細**評価に失敗した対象インスタンスの横にあるウィンドウです。 チェック ボックスのいずれかが選択されている場合、**適用**ボタンができるようになります。 クリックすると、**適用**、非対応の設定が自動的に選択したターゲット インスタンスに更新されます。  
  
    > [!CAUTION]  
    >  ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。 1 つ以上のチェック ボックスを選択すると、クリックすることをお勧め**スクリプト**、出力場所を選択して、基になるを確認するようにして[!INCLUDE[tsql](../includes/tsql-md.md)]コードの変更を適用する前にします。  
  
8.  ポリシーの詳細な結果を表示するでのポリシーをクリックして、**結果**テーブル。 **対象の詳細**テーブルには、インスタンスごとに詳細が表示されます。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a>参照  
 [監視し、ポリシー ベースの管理を使用して、ベスト プラクティスを適用](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)   
 [中央管理サーバーを使用した複数のサーバーの管理](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  