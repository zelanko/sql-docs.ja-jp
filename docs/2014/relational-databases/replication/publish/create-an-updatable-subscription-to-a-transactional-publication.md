---
title: Create an Updatable Subscription to a Transactional Publication (Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2014
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
caps.latest.revision: 46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b6a3e276eb1250938e882316f84cf61f49a5b7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290468"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a>トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio)

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
**サブスクリプションの新規作成ウィザード**の **[更新可能なサブスクリプション]** ページで、更新可能なサブスクリプションを構成します。 このページは、更新可能なサブスクリプションに対してトランザクション パブリケーションを有効にした場合にのみ使用できます。 更新可能なサブスクリプションを有効にする方法については、「[トランザクション パブリケーションの更新サブスクリプションを有効にする方法](enable-updating-subscriptions-for-transactional-publications.md)」を参照してください。   
  
## <a name="to-configure-an-updatable-subscription-from-the-publisher"></a>パブリッシャーから更新可能なサブスクリプションを構成するには  

1. Microsoft SQL Server Management Studio でパブリッシャーに接続し、サーバー ノードを展開します。

2. **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。

3. 更新サブスクリプションを有効にしたトランザクション パブリケーションを右クリックし、**[新しいサブスクリプション]** をクリックします。

4. ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。

5. **サブスクリプションの新規作成ウィザード**の **[更新可能なサブスクリプション]** ページで、**[レプリケート]** が選択されていることを確認します。

6. **[パブリッシャーでのコミット]** ボックスの一覧からオプションを選択します。

    * 即時更新サブスクリプションを使用するには、**[変更を同時にコミットする]** を選択します。 このオプションを選択し、パブリケーションがキュー更新サブスクリプションを許可する場合 (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクリプション プロパティ **update_mode** は **failover** に設定されます。 このモードでは、必要に応じて、後からキュー更新に切り替えることができます。

    * キュー更新サブスクリプションを使用するには、**[変更をキューに登録し、可能な場合はコミット]** を選択します。 このオプションを選択し、パブリケーションが即時更新サブスクリプションを許可していて (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクライバーが SQL Server 2005 以降を実行している場合、サブスクリプション プロパティ **update_mode** は queued failover に設定されます。 このモードでは、必要に応じて、後から即時更新に切り替えることができます。

    更新モードの切り替えの詳細については、「[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)」(更新可能なトランザクション サブスクリプションの更新モードを切り替える) を参照してください。

7. 即時更新を使用するサブスクリプション、または **update_mode** を **queued failover** に設定したサブスクリプションに対して **[更新可能なサブスクリプション用のログイン]** ページが表示されます。 **[更新可能なサブスクリプション用のログイン]** ページで、即時更新サブスクリプション用にパブリッシャーへの接続を作成するリンク サーバーを指定します。 接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。 以下のオプションの 1 つを選択します。

    * **[SQL Server 認証を使用して接続するリンク サーバーを作成する]**。 サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。

    * **[定義済みのリンク サーバーまたはリモート サーバーを使用する]** [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio、または他の方法を使用してサブスクライバ―とパブリッシャーの間にリモート サーバーまたはリンクされたサーバーを定義した場合は、このオプションを選択します。

    リンクされたサーバー アカウントに必要な権限に関する詳細については、「[ここにサブスクリプションを入力](../security/secure-the-subscriber.md)」の「**Queued Updating Subscriptions**」(キューに入れられた更新サブスクリプション) を参照してください。

8. ウィザードを完了します。

## <a name="to-configure-an-updatable-subscription-from-the-subscriber"></a>サブスクライバーから更新可能なサブスクリプションを構成するには


1. SQL Server Management Studio でサブスクライバ―に接続し、サーバー ノードを展開します。

2. **[レプリケーション]** フォルダーを展開します。

3. **[ローカル サブスクリプション]** フォルダーを右クリックし、 **[新しいサブスクリプション]** をクリックします。

4. **サブスクリプションの新規作成ウィザード**の **[パブリケーション]** ページで、**[パブリッシャー]** ボックスの一覧から **[<SQL Server パブリッシャーの検索>]** を選択します。

5. **[サーバーへの接続]** ダイアログ ボックスでパブリッシャーに接続します。

6. **[パブリケーション]** ページで、更新サブスクリプションを有効にしたトランザクション パブリケーションを選択します。

7. ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。

8. サブスクリプションの新規作成ウィザードの **[更新可能なサブスクリプション]** ページで、**[レプリケート]** が選択されていることを確認します。

9. **[パブリッシャーでのコミット]** ボックスの一覧からオプションを選択します。

    * 即時更新サブスクリプションを使用するには、**[変更を同時にコミットする]** を選択します。 このオプションを選択し、パブリケーションがキュー更新サブスクリプションを許可する場合 (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクリプション プロパティ **update_mode** は **failover** に設定されます。 このモードでは、必要に応じて、後からキュー更新に切り替えることができます。

    * キュー更新サブスクリプションを使用するには、**[変更をキューに登録し、可能な場合はコミット]** を選択します。 このオプションを選択し、パブリケーションが即時更新サブスクリプションを許可していて (パブリケーションの新規作成ウィザードを使用して作成されたパブリケーションの既定値)、サブスクライバーが SQL Server 2005 以降を実行している場合、サブスクリプション プロパティ **update_mode** は queued **failover** に設定されます。 このモードでは、必要に応じて、後から即時更新に切り替えることができます。

    更新モードの切り替えの詳細については、「[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)」(更新可能なトランザクション サブスクリプションの更新モードを切り替える) を参照してください。

10. 即時更新を使用するサブスクリプション、または **update_mode** を queued **failover** に設定したサブスクリプションに対して **[更新可能なサブスクリプション用のログイン]** ページが表示されます。 **[更新可能なサブスクリプション用のログイン]** ページで、即時更新サブスクリプション用にパブリッシャーへの接続を作成するリンク サーバーを指定します。 接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。 以下のオプションの 1 つを選択します。

    * **[SQL Server 認証を使用して接続するリンク サーバーを作成する]**。 サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。

    * **[定義済みのリンク サーバーまたはリモート サーバーを使用する]** [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio、または他の方法を使用してサブスクライバ―とパブリッシャーの間にリモート サーバーまたはリンクされたサーバーを定義した場合は、このオプションを選択します。

    リンクされたサーバー アカウントに必要な権限に関する詳細については、「[ここにサブスクリプションを入力](../security/secure-the-subscriber.md)」の「**Queued Updating Subscriptions**」(キューに入れられた更新サブスクリプション) を参照してください。

11. ウィザードを完了します。

## <a name="see-also"></a>参照

[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)

[パブリケーションの作成](create-a-publication.md)

[Transact-SQL を使用してトランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](../create-updatable-subscription-transactional-publication-transact-sql.md) 
 
  
