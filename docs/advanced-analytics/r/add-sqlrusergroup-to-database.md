---
title: データベース ユーザー (SQL Server の Machine Learning) として SQLRUserGroup を追加 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f0877f04b35475dd4d1403390447adad0c3936c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203134"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>SQLRUserGroup をデータベース ユーザーとして追加します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、データベースに接続し、ユーザーの代理として R または Python のジョブを実行するアクセス許可が必要な SQL Server の machine learning のサービスで使用されるワーカー アカウントのグループに付与する方法について説明します。

## <a name="what-is-sqlrusergroup"></a>SQLRUserGroup とは何ですか。

セットアップ時に[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]または[!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]R の実行をサポートするために新しい Windows ユーザー アカウントを作成、または Python スクリプトのセキュリティ トークンのタスクは、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービス。

これらのアカウントを表示するには、Windows ユーザー グループに**SQLRUserGroup**です。 既定では、20 のワーカー アカウントが作成された、機械学習を実行するために十分な数より多くのジョブは通常です。

ユーザーは、機械学習、外部クライアントからのスクリプトを送信するとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用可能なワーカー アカウントがアクティブ化、呼び出し元のユーザーの id にマップし、ユーザーの代理としてスクリプトを実行します。 データベース エンジンのこの新しいサービスが、セキュリティで保護された外部スクリプトの実行と呼ばれるをサポートしている*黙示的な認証*です。

ただし、リモート データ サイエンス クライアントから R または Python スクリプトを実行する必要があるあり、Windows 認証を使用している、付ける必要がありますこれらのワーカー アカウントにサインインするアクセス許可、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あなたの代理としてのインスタンス。

## <a name="add-sqlrusergroup-as-a-sql-server-login"></a>SQL Server ログインとして SQLRUserGroup を追加します。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]** を展開し、 **[ログイン]** を右クリックして、 **[新しいログイン]** を選択します。

2. **ログイン - 新規**ダイアログ ボックスで、**検索**です。 (何も入力しないでボックスで、まだ。)
    
     ![機械学習の新しいログインの追加の検索 をクリックして](media/implied-auth-login1.png "機械学習の新しいログインの追加の検索 をクリックして")

3. **ユーザーまたはグループ**ボックスで、クリックして、**オブジェクトの種類**ボタンをクリックします。

     ![機械学習の新しいログインを追加するオブジェクトの種類を検索](media/implied-auth-login2.png "機械学習の新しいログインを追加するオブジェクトの種類を検索")

4. **オブジェクトの種類**ダイアログ ボックスで、**グループ**です。 その他のすべてのチェック ボックスをオフにします。

     ![オブジェクトの種類 ダイアログ ボックスでグループを選択](media/implied-auth-login3.png "オブジェクトの種類] ダイアログ ボックスで [グループの選択")

4. をクリックして**詳細**、検索する場所がクリックして、現在のコンピューターであることを確認**今すぐ検索**です。

     ![グループの一覧を取得するには、今すぐ検索](media/implied-auth-login4.png "をクリックして今すぐ検索のグループの一覧を取得するには")

5. 1 つの先頭に表示されるまで、サーバー上のグループ アカウントの一覧をスクロール`SQLRUserGroup`です。
    
    + スタート パッド サービスに関連付けられているグループの名前、_既定のインスタンス_は常に**SQLRUserGroup**R、Python またはその両方をインストールするかどうかに関係なく、します。 このアカウントの既定のインスタンスのみを選択します。
    + 使用している場合、_名前付きインスタンス_、インスタンス名が既定の作業者グループ名の名前に追加されます`SQLRUserGroup`です。 そのため場合、インスタンスは、"MLTEST"という名前は、このインスタンスの既定のユーザー グループ名になります**SQLRUserGroupMLTest**です。
 
     ![サーバー上のグループの使用例](media/implied-auth-login5.png "サーバー上のグループの例")
   
5. をクリックして**OK**高度な検索 ダイアログ ボックスを閉じます。

    > [!IMPORTANT]
    > インスタンスの正しいアカウントを選択したことを確認します。 各インスタンスには、独自のスタート パッド サービスだけとそのサービスに対して作成されたグループを使用できます。 インスタンスには、スタート パッド サービスまたはワーカー アカウントを共有できません。

6. をクリックして**OK**を閉じるにはもう一度、 **[ユーザーまたはグループ**] ダイアログ ボックス。

7. **ログイン - 新規**ダイアログ ボックスで、をクリックして**OK**です。 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。

## <a name="change-the-number-of-worker-accounts-in-sqlrusergroup"></a>SQLRUserGroup のワーカー アカウント数を変更します。

機械学習の頻繁に使用する場合は、この記事の内容の説明に従って外部のスクリプトを実行するために使用するアカウントの数を増やすことができます。 

+ [機械学習のユーザー アカウント プールを変更します。](modify-the-user-account-pool-for-sql-server-r-services.md)

既定では、20 のアカウントが作成になり、20 の同時実行セッションをサポートします。 並列化されたタスクは、追加のアカウントを使用しません。 たとえば、ユーザーは、並列処理を使用するスコア付けタスクを実行する場合は、すべてのスレッドのワーカーと同じアカウントが再利用されます。
