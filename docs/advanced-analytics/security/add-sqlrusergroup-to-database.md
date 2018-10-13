---
title: データベース ユーザー (SQL Server Machine Learning) としての SQLRUserGroup の追加 |Microsoft Docs
description: SQL Server Machine Learning Services のデータベース ユーザーとしての SQLRUserGroup を追加する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fc5294453def64d13cc43a74a8a5fb299c3e23e3
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100323"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>データベース ユーザーとしての SQLRUserGroup の追加
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データベース ログインを作成、 [SQLRUserGroup](../concepts/security.md#sqlrusergroup)ターゲットがデータまたは SQL Server インスタンスに対する操作の場合は、R と Python スクリプトから送信された信頼関係接続を許可します。 

SQL Server ログインで接続文字列、または完全に指定されたユーザー名とパスワードを含むスクリプトでは、ログインを作成する必要はありません。

## <a name="when-a-login-is-required"></a>ログインが必要な場合

R または Python スクリプトには、信頼関係接続を指定する接続文字列が含まれている場合 (たとえば、"Trusted_Connection = True")、追加の構成は、ユーザー id の適切なプレゼンテーションの SQL Server に必要です。 外部のプロセスで実行されているため、 **SQLRUserGroup** MSSQLSERVER01、信頼されたユーザーなどのワーカー アカウントは、worker の id として表示されます。 この id に SQL Server へのログイン権限があるないために、追加しない限り接続が失敗する信頼された**SQLRUserGroup**データベース ユーザーとして。 詳細については、次を参照してください。 [*暗黙の認証*](../../advanced-analytics/concepts/security.md#implied-authentication)します。

スタート パッドがスクリプトとプロセスを実行するワーカー アカウントを起動した元のユーザーのマッピングを保持することを思い出してください。 ワーカー アカウントの信頼関係接続が完了すると、元の呼び出し元ユーザーの id が引き継ぎ、データを取得するために使用します。 Db_datareader 権限を付与する必要はありません**SQLRUserGroup**します。

> [!Note]
>  必ず**SQLRUserGroup** 「ローカル ログオンを許可」権限します。 既定では、すべての新しいローカル ユーザーにこの権限が与えられますが、一部の組織では、厳しいグループ ポリシーを適用する場合があります。

## <a name="create-a-login"></a>ログインを作成します

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]** を展開し、 **[ログイン]** を右クリックして、 **[新しいログイン]** を選択します。

2. **ログイン - 新規**ダイアログ ボックスで、**検索**します。 (何も入力しないでボックスで、まだ。)
    
     ![Machine learning の新しいログインの追加の検索 をクリックして](media/implied-auth-login1.png "machine learning の新しいログインを追加する検索をクリックします。")

3. **ユーザーまたはグループ**ボックスで、、**オブジェクトの種類**ボタンをクリックします。

     ![Machine learning の新しいログインを追加するオブジェクトの種類を検索](media/implied-auth-login2.png "machine learning の新しいログインを追加するオブジェクトの種類の検索")

4. **オブジェクトの種類**ダイアログ ボックスで、**グループ**します。 その他のすべてのチェック ボックスをオフにします。

     ![オブジェクトの種類 ダイアログ ボックスでグループを選択します](media/implied-auth-login3.png "オブジェクトの種類] ダイアログ ボックスで [グループの選択。")

4. クリックして**詳細**を検索する場所がクリックして、現在のコンピューターであることを確認**検索開始**します。

     ![グループの一覧を取得するには、今すぐ検索](media/implied-auth-login4.png "クリックして検索開始のグループの一覧を取得するには")

5. 以降の 1 つが表示されるまで、サーバー上のグループ アカウントの一覧をスクロール`SQLRUserGroup`します。
    
    + スタート パッド サービスに関連付けられているグループの名前、_既定のインスタンス_は常に**SQLRUserGroup**R または Python をインストールするかどうかに関係なく、します。 このアカウントの既定のインスタンスのみを選択します。
    + 使用する場合、_名前付きインスタンス_、インスタンス名の既定の worker グループの名前、名前に追加されます`SQLRUserGroup`します。 そのため、インスタンスは、"MLTEST"という名前は、このインスタンスの既定のユーザー グループ名なります**SQLRUserGroupMLTest**します。
 
     ![サーバーのグループの例](media/implied-auth-login5.png "サーバー上のグループの例")
   
5. クリックして**OK**高度な検索 ダイアログ ボックスを閉じます。

    > [!IMPORTANT]
    > インスタンスの正しいアカウントを選択したことを確認します。 各インスタンスには、独自のスタート パッド サービスだけとそのサービスに対して作成されたグループを使用できます。 インスタンスは、スタート パッド サービスまたはワーカー アカウントを共有できません。

6. をクリックして**OK**を閉じるにはもう一度、 **[ユーザーまたはグループ**] ダイアログ ボックス。

7. **ログイン - 新規**ダイアログ ボックスで、をクリックして**OK**。 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。