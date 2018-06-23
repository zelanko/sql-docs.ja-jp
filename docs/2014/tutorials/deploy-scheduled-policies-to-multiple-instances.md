---
title: スケジュールされたポリシーを複数のインスタンスに配置 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8331f0f33874c5bfbd0811231dc2cacf494b1d89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173597"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>スケジュールされたポリシーの複数インスタンスへの配置
  登録済みサーバーを使用すると、スケジュールされたポリシーを集中管理された場所からマネージ サーバーに配置できます。 スケジュールされたポリシーは、ローカル サーバー グループまたは中央管理サーバーから配置できます。  
  
 ここでは、次の作業を行います。  
  
1.  前の作業でスケジュール設定したポリシーをフォルダーにエクスポートします。  
  
2.  登録済みサーバーで管理されている対象インスタンスにスケジュールされたポリシーを配置します。  
  
 これらの作業は、このレッスンの前の作業を完了したコンピューターで実行します。  
  
## <a name="prerequisites"></a>前提条件  
 この作業には、次の前提条件があります。  
  
-   このレッスンの前の作業を完了している必要があります。  
  
-   スケジュールされたポリシーを配置するインスタンスで [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降を実行している必要があります。 オートメーションではポリシーがローカルに格納されている必要がありますが、これは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ではサポートされていません。  
  
-   スケジュールされたポリシーを展開するサーバーは、いずれかで登録済みサーバーに登録する必要があります、**ローカル サーバー グループ**または**中央管理サーバー**ノード。 詳細については、次の各トピックを参照してください。  
  
    -   [サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [接続のサーバーの登録&#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)です。  
  
    -   [中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>スケジュールされたポリシーを .xml ファイルとしてエクスポートするには  
  
1.  前の作業でスケジュールされたポリシーを構成したサーバーで展開**管理**、展開**ポリシーの管理**、順にクリック**ポリシー**です。  
  
2.  **[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックします。  
  
3.  **オブジェクト エクスプ ローラーの詳細** ウィンドウで、スケジュールされたベスト プラクティスを登録済みサーバーを通じてその他のサーバーに展開するポリシーをすべて選択します。  
  
    > [!NOTE]  
    >  クリックすることができます、**カテゴリ**見出しをカテゴリで、ポリシーを並べ替えます。  
  
4.  選択範囲を右クリックし、をクリックして**ポリシーのエクスポート**です。  
  
5.  エクスポートするのに複数のポリシーを選択した場合、**フォルダーの参照**ダイアログ ボックスで、コピー先フォルダーを選択するか、新しいフォルダーを作成します。 このレッスンでは、パスに新しいフォルダーを作成**C:\Scheduled_BP_Policies**、クリックして**OK**です。  
  
     のみで、エクスポートする 1 つのポリシーを選択した場合、**ポリシーのエクスポート**  ダイアログ ボックスで、パスに新しいフォルダーを作成**C:\Scheduled_BP_Policies**、 をクリックして**開く**をクリックし、**保存**です。  
  
     .xml ポリシー ファイルがフォルダーの場所に作成されます。  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>登録済みサーバーで管理されているサーバーにスケジュールされたポリシーを配置するには  
  
1.  **[表示]** メニューの **[登録済みサーバー]** をクリックします。  
  
2.  展開**データベース エンジン**、いずれかを展開**ローカル サーバー グループ**または**中央管理サーバー**のポリシーを展開するノードを右クリックし、をクリックして**ポリシーのインポート**です。  
  
    > [!NOTE]  
    >  右クリックした場合**ローカル サーバー グループ**または中央管理サーバー自体には、ポリシーはすべての管理対象サーバーに配置されます。 特定のサーバー グループを右クリックした場合、そのグループ内のサーバーだけにポリシーが配置されます。 特定の登録済みサーバーを右クリックした場合、そのサーバーだけにポリシーが配置されます。  
  
3.  横に**ファイルをインポートする**、省略記号ボタンをクリックして (**.**).  
  
4.  **ポリシーの選択** ダイアログ ボックスで、スケジュールされたポリシーを保存したフォルダーの場所を参照します。 この例では、場所を参照**C:\Scheduled_BP_Policies**です。  
  
5.  ポリシー対象インスタンスにインポートし、をクリックするを選択する**開く**です。  
  
6.  **インポート** ダイアログ ボックスで、**ポリシーの状態**一覧で、目的のポリシーの状態を選択します。 ポリシーの状態を保存するか、インポート時にポリシーを有効または無効にするかを選択することができます。 ポリシーは、スケジュールに従って実行されるように有効にしておく必要があることに注意してください。  
  
7.  をクリックして**OK**すべてのターゲット インスタンスにポリシーをインポートします。  
  
    > [!NOTE]  
    >  任意のエラーがある場合、**インポート** ダイアログ ボックスが非表示になりません。 クリックして、**ログ**ページにメッセージを確認します。 をクリックして**キャンセル**ダイアログ ボックスを閉じます。  
  
8.  対象インスタンスからポリシーを表示するには、インスタンスへの接続でオブジェクト エクスプ ローラーを開き、展開**管理**の順に展開および**ポリシー**です。 インポートされたポリシーを確認する必要があります、**ポリシー**ノード。 各ポリシーをダブルクリックすると、スケジュールを表示したり、設定を変更したりすることができます。  
  
    > [!NOTE]  
    >  スケジュールされたポリシーが実行された後に評価結果を表示するには、対象インスタンスのポリシー履歴ログを開きます。 ログを開くを右クリックして**ポリシーの管理**、クリックして**履歴を表示する**です。  
  
## <a name="summary"></a>まとめ  
 このチュートリアルでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスに対して、ベスト プラクティス ポリシーの評価を要求時および定期的に実行する方法について学習しました。  
  
## <a name="next"></a>Next  
 このチュートリアルはこれで終了です。 開始に戻り、次を参照してください。[チュートリアル: ポリシー管理でのベスト プラクティスの評価](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)です。  
  
 一覧を表示する[!INCLUDE[ssDE](../includes/ssde-md.md)]チュートリアルについてをクリックして[データベース エンジンのチュートリアル](../relational-databases/database-engine-tutorials.md)です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  