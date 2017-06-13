---
title: "レポート サーバーへのアクセスを許可 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a92c37165b8142b7e96a8bb99dee43ea5f12e247
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="grant-user-access-to-a-report-server"></a>レポート サーバーにユーザー アクセスの許可

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、ロール ベースのセキュリティを使用して、レポート サーバーへのアクセス権がユーザーに付与されます。 新しいレポート サーバーをインストールした直後は、ローカル Administrators グループに属するユーザーにのみ、レポート サーバーのコンテンツと操作に対する権限が与えられます。 他のユーザーがレポート サーバーにアクセスできるようにするには、ロール割り当てを作成して、ユーザーまたはグループ アカウントを、一連のタスクが指定された定義済みのロールにマップする必要があります。

 **SharePoint モードのレポート サーバー:** SharePoint 統合モード用に構成されたレポート サーバーの場合は、SharePoint サイトから、SharePoint の権限を使ってアクセスを構成します。 レポート サーバーのコンテンツや操作にアクセスできるかどうかは、SharePoint サイト上の権限レベルによって決まります。 SharePoint サイトでの権限を付与できるのはサイト管理者だけです。 詳細については、「 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)」を参照してください。

 **ネイティブ モードのレポート サーバー:**このトピックは、ネイティブ モードと、ユーザーをロールに割り当てる、web ポータルの使用が構成されているレポート サーバーに重点を置きます。 ロールには次の 2 種類があります。

- アイテムレベルのロール : レポート サーバーのコンテンツ、サブスクリプション、レポート処理、レポート履歴などを表示、追加、および管理するためのロール。 アイテム レベルのロール割り当ては、ルート ノード ([ホーム] フォルダー)、または階層内でそれより下位にある特定のフォルダーやアイテムに対して定義できます。

- システムレベルのロール : 特定のアイテムではなく、サイト全体にわたる操作へのアクセスを許可します。 たとえば、レポート ビルダーや共有スケジュールを使用することが含まれます。

    この 2 種類のロールは相互補完的な関係にあり、組み合わせて使用する必要があります。 そのため、レポート サーバーにユーザーを追加するには、2 段階の処理が必要となります。 ユーザーをアイテムレベルのロールに割り当てる場合は、同時にシステムレベルのロールにも割り当てる必要があります。 ユーザーをロールに割り当てる際は、既に定義されているロールを選択する必要があります。 ロールを作成、変更、または削除するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用します。 詳細については、「[ロールを作成、削除、または変更する (Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md)」を参照してください。

## <a name="before-you-start"></a>開始前の準備

ネイティブ モードのレポート サーバーにユーザーを追加する場合は、あらかじめ次の点を確認してください。

- レポート サーバー コンピューターのローカル Administrators グループのメンバーとしてログインする必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] または Windows Server 2008 に配置する場合、レポート サーバーをローカルで管理するには追加の構成が必要となります。 詳細については、次を参照してください。[をローカル管理用のネイティブ モード レポート サーバーを構成する](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)です。

- このタスクを他のユーザーに委任する場合は、ユーザー アカウントをコンテンツ マネージャー ロールとシステム管理者ロールにマップするためのロール割り当てを作成します。 コンテンツ マネージャーとシステム管理者の権限を与えられたユーザーは、レポート サーバーにユーザーを追加できます。

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、システム ロールおよびユーザー ロールに対して定義されているロールを確認し、それぞれのロールにどのようなタスクが含まれているかを確認します。 ように、ユーザーの追加を開始する前の役割について理解しておくにも、タスクの説明は、web ポータルに表示されません。

- 必要であれば、ロールをカスタマイズするか、新しいロールを定義して必要なタスクを追加します。 たとえば、個々のアイテムにカスタム セキュリティ設定を使用する場合は、フォルダーの閲覧権限を付与した新しいロール定義を作成する必要があります。

### <a name="to-add-a-user-or-group-to-a-system-role"></a>ユーザーまたはグループをシステム ロールに追加するには

1. 開始、 [web ポータル](../web-portal-ssrs-native-mode.md)です。

2. 選択、*歯車アイコン*右上にします。

3. **[サイトの設定]**を選択します。

4. **[セキュリティ]**を選択します。

5. 選択**グループの追加またはユーザー**です。

6. **グループまたはユーザー**Windows ドメイン ユーザー名を入力、または、この形式でアカウントをグループ化:\<ドメイン >\\< アカウント\>です。 

    > [!NOTE]
    > フォーム認証やカスタム セキュリティを使用している場合は、その環境に合った適切な形式でユーザー アカウントまたはグループ アカウントを指定します。

7. システムの役割を選択し、 **OK**です。

    ロールは累積されます。したがって、システム管理者とシステム ユーザーを両方とも選択した場合、そのユーザーまたはグループは、これら両方のロールのタスクを実行できるようになります。

8. 割り当てを作成するユーザーまたはグループが他にもある場合は、以上の手順を繰り返します。

### <a name="to-add-a-user-or-group-to-an-item-role"></a>ユーザーまたはグループをアイテム ロールに追加するには

1. 開始、 **web ポータル**し、ユーザーまたはグループを追加するレポート アイテムを探します。

2. 選択、**しています.** (楕円) 項目でします。

3. ドロップダウン メニューで、次のように選択します。**管理**です。

4. **[セキュリティ]**を選択します。

5. 選択**グループの追加またはユーザー**です。

    > [!NOTE]
    > 現在のアイテムは親アイテムからセキュリティを継承する場合、は、選択**セキュリティをカスタマイズ**セキュリティ設定を変更するには、ツールバーでします。 選択し、**グループの追加またはユーザー**です。

6. **グループまたはユーザー**Windows ドメイン ユーザー名を入力、または、この形式でアカウントをグループ化:\<ドメイン >\\< アカウント\>です。 フォーム認証やカスタム セキュリティを使用している場合は、その環境に合った適切な形式でユーザー アカウントまたはグループ アカウントを指定します。

7. 方法について説明して、ユーザーまたはグループは、アイテムにアクセスするを選択し、1 つまたは複数のロールの定義を選択して**OK**です。

8. 割り当てを作成するユーザーまたはグループが他にもある場合は、以上の手順を繰り返します。

## <a name="next-steps"></a>次の手順

[ロールの割り当てを作成および管理する](../../reporting-services/security/create-and-manage-role-assignments.md)   
[ロールの割り当て ページ &#40; 新しいロールの割り当てを編集します。レポート マネージャー &#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[セキュリティのプロパティ ページ、項目 & #40 です。レポート マネージャー &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[ロールの割り当て](../../reporting-services/security/role-assignments.md)   
[ロールの定義](../../reporting-services/security/role-definitions.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
