---
title: "トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新可能トランザクション サブスクリプション"
  - "更新可能トランザクション サブスクリプション、SSMS"
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio)

> [!NOTE]  
>  この機能は、[!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] 2012 から 2016 のバージョンでサポートされています。  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
更新可能なサブスクリプションを構成、 **更新可能なサブスクリプション** のページ、 **サブスクリプション新規作成ウィザード**します。 このページは、更新可能なサブスクリプションに対してトランザクション パブリケーションを有効にした場合にのみ使用できます。 更新可能なサブスクリプションを有効にする方法の詳細については、次を参照してください。 [トランザクション パブリケーションのサブスクリプションの更新を有効にする](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)です。   
  
## パブリッシャーから更新可能なサブスクリプションを構成するには  

1. Microsoft SQL Server Management Studio でパブリッシャーに接続し、サーバー ノードを展開します。

2. **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。

3. 更新サブスクリプションを有効になっているトランザクション パブリケーションを右クリックし、をクリックし、 **新規サブスクリプション**します。

4. ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。

5. **更新可能なサブスクリプション** のページ、 **サブスクリプション新規作成ウィザード**, 、ように **レプリケート** が選択されています。

6. オプションを選択、 **パブリッシャーでコミット** ボックスの一覧。

    * 即時更新サブスクリプションを使用する選択 **同時に変更をコミット**します。 このオプションを選択すると、パブリケーションでキュー更新サブスクリプション (パブリケーションの新規作成ウィザードで作成されたパブリケーションの既定)、サブスクリプションのプロパティ **update_mode** に設定されている **フェールオーバー**します。 このモードでは、必要に応じて、後からキュー更新に切り替えることができます。

    * キュー更新サブスクリプションを使用する選択 **キューに変更して、コミット可能であれば**します。 このオプションを選択し、パブリケーションで即時更新サブスクリプション (パブリケーションの新規作成ウィザードで作成されたパブリケーションの既定) とサブスクライバーには、SQL Server 2005 またはそれ以降のサブスクリプションのプロパティが実行されている場合 **update_mode** キューに置かれたフェールオーバーに設定されています。 このモードでは、必要に応じて、後から即時更新に切り替えることができます。

    更新モードの切り替えについては、次を参照してください。 [の更新モードの切り替え更新可能トランザクション サブスクリプションの](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)です。

7. **更新可能なサブスクリプション用のログイン** 即時更新を使用することもがサブスクリプションのページが表示されます **update_mode** に設定 **フェイル オーバーをキューに置かれた**です。 **更新可能なサブスクリプション用のログイン** ページで、即時更新サブスクリプションの対象で、パブリッシャーへの接続が行われたリンク サーバーを指定します。 接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。 以下のオプションの 1 つを選択します。

    * **SQL Server 認証を使用して接続するリンク サーバーを作成します。** サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。

    * **[定義済みのリンク サーバーまたはリモート サーバーを使用する]** リモート サーバーまたは、サブスクライバーとパブリッシャーを使用して、間にリンク サーバー定義している場合は、このオプションを選択 [sp_addserver (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), 、[sp_addlinkedserver (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), 、SQL Server Management Studio、または別の方法です。

    リンク サーバー アカウントに必要な権限については、次を参照してください。、 **キュー更新サブスクリプション** の [リンクの説明は、ここに入力](../../../relational-databases/replication/security/secure-the-subscriber.md)します。

8. ウィザードを完了します。

## サブスクライバーから更新可能なサブスクリプションを構成するには


1. SQL Server Management Studio でサブスクライバーに接続し、サーバー ノードを展開します。

2. **[レプリケーション]** フォルダーを展開します。

3. 右クリックし、 **ローカル サブスクリプション** フォルダー、およびクリック **新規サブスクリプション**します。

4. **パブリケーション** のページ、 **サブスクリプション新規作成ウィザード**, [ **SQL Server パブリッシャーの検索** から、 **パブリッシャー** ドロップダウン リストです。

5. **[サーバーへの接続]** ダイアログ ボックスでパブリッシャーに接続します。

6. 更新サブスクリプションを有効になっているトランザクション パブリケーションを選択して、 **パブリケーション** ページです。

7. ウィザード内のページに従って、ディストリビューション エージェントが実行される場所など、サブスクリプションに対するオプションを指定します。

8. **更新可能なサブスクリプション** ページのサブスクリプションの新規作成ウィザード、 **レプリケート** が選択されています。

9. オプションを選択、 **パブリッシャーでコミット** ボックスの一覧。

    * 即時更新サブスクリプションを使用する選択 **同時に変更をコミット**します。 このオプションを選択すると、パブリケーションでキュー更新サブスクリプション (パブリケーションの新規作成ウィザードで作成されたパブリケーションの既定)、サブスクリプションのプロパティ **update_mode** に設定されている **フェールオーバー**します。 このモードでは、必要に応じて、後からキュー更新に切り替えることができます。

    * キュー更新サブスクリプションを使用する選択 **キューに変更して、コミット可能であれば**します。 このオプションを選択し、パブリケーションで即時更新サブスクリプション (パブリケーションの新規作成ウィザードで作成されたパブリケーションの既定) とサブスクライバーには、SQL Server 2005 またはそれ以降のサブスクリプションのプロパティが実行されている場合 **update_mode** にキューに置かれた設定 **フェールオーバー**します。 このモードでは、必要に応じて、後から即時更新に切り替えることができます。

    更新モードの切り替えについては、次を参照してください。 [の更新モードの切り替え更新可能トランザクション サブスクリプションの](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)です。

10. **更新可能なサブスクリプション用のログイン** 即時更新を使用することもがサブスクリプションのページが表示されます **update_mode** 設定にキューに置かれた **フェールオーバー**します。 **更新可能なサブスクリプション用のログイン** ページで、即時更新サブスクリプションの対象で、パブリッシャーへの接続が行われたリンク サーバーを指定します。 接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。 以下のオプションの 1 つを選択します。

    * **SQL Server 認証を使用して接続するリンク サーバーを作成します。** サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。

    * **[定義済みのリンク サーバーまたはリモート サーバーを使用する]** リモート サーバーまたは、サブスクライバーとパブリッシャーを使用して、間にリンク サーバー定義している場合は、このオプションを選択 [sp_addserver (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), 、[sp_addlinkedserver (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), 、SQL Server Management Studio、または別の方法です。

    リンク サーバー アカウントに必要な権限については、次を参照してください。、 **キュー更新サブスクリプション** の [リンクの説明は、ここに入力](../../../relational-databases/replication/security/secure-the-subscriber.md)します。

11. ウィザードを完了します。

## 参照

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)

[Transact-SQL を使用してトランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](../../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) 
