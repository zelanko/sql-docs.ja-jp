---
title: データベース ユーザーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055435"
---
# <a name="create-a-database-user"></a>データベース ユーザーの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、ログインにマップされるデータベース ユーザーを作成する方法について説明します。 データベース ユーザーは、ログインの ID として、データベースへの接続時に使用されます。 データベース ユーザーとログインには同じ名前を使用できますが、必ずしもその必要はありません。 このトピックは、既存のログインが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に存在することを前提としています。 ログインの作成方法の詳細については、「[ログインの作成](create-a-login.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [背景](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **次のものを使用してデータベース ユーザーを作成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="background"></a><a name="Restrictions"></a>の背景情報  
 ユーザーは、データベース レベルのセキュリティ プリンシパルです。 データベースに接続するためには、データベース ユーザーにログインをマップする必要があります。 異なるデータベースには、1 つのログインを異なるユーザーとしてマップすることができますが、各データベースでは 1 人のユーザーとしてのみマップできます。 部分的包含データベースでは、ログインを持たないユーザーを作成できます。 包含データベース ユーザーの詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。 データベースで guest ユーザーが有効になっている場合は、データベース ユーザーにマップされていないログインでも、guest ユーザーとしてそのデータベースにアクセスすることができます。  
  
> [!IMPORTANT]  
>  guest ユーザーは無効にするのが一般的です。 必要な場合を除き、guest ユーザーは有効にしないでください。  
  
 セキュリティ プリンシパルとして、ユーザーには権限を許可することができます。 ユーザーのスコープはデータベースです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンス上の特定のデータベースに接続するには、データベース ユーザーにログインをマップする必要があります。 データベース内の権限を許可したり拒否したりする際に、その対象となるのは、ログインではなく、データベース ユーザーです。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 データベースに対する `ALTER ANY USER` 権限が必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
##### <a name="to-create-a-database-user"></a>データベース ユーザーを作成するには  
  
1.  オブジェクト エクスプローラーで、 **[データベース]** フォルダーを展開します。  
  
2.  新しいデータベース ユーザーを作成するデータベースを展開します。  
  
3.  **[セキュリティ]** フォルダーを右クリックし、**[新規作成]** をポイントして、**[ユーザー]** を選択します。  
  
4.  [**データベースユーザー-新規作成**] ダイアログボックスの **[全般**] ページで、[**ユーザーの種類**] ボックスの一覧から [ユーザーの種類] ボックスの一覧から1つを選択します。 [ログインを使用し**た sql**ユーザー]、[**ログインを持たない sql ユーザー**]、**証明書にマップ**されたユーザー、**非対称キーにマップ****されて**いるユーザー  
  
5.  **[ユーザー名]** ボックスに、新しいユーザーの名前を入力します。 [**ユーザーの種類**] ボックスの一覧から [ **Windows ユーザー** ] を選択した場合は、参照ボタン ([...] **)** をクリックして [**ユーザーまたはグループの選択**] ダイアログボックスを開くこともできます。  
  
6.  **[ログイン名]** ボックスにユーザーのログインを入力します。 または、省略記号 **[...]** をクリックして **[ログインの選択]** ダイアログ ボックスを開きます。 **[ログイン名]** は、 **[ユーザーの種類]** で一覧から **[ログインを持つ SQL ユーザー]** または **[Windows ユーザー]** を選択した場合に使用できます。  
  
7.  **[既定のスキーマ]** ボックスで、このユーザーが作成したオブジェクトを所有するスキーマを指定します。 または、省略記号 **[...]** をクリックして **[スキーマの選択]** ダイアログ ボックスを開きます。 **[既定のスキーマ]** は、 **[ユーザーの種類]** で一覧から **[ログインを持つ SQL ユーザー]**、 **[ログインを持たない SQL ユーザー]** 、または **[Windows ユーザー]** を選択した場合に使用できます。  
  
8.  **[証明書名]** ボックスに、データベース ユーザーに使用する証明書を入力します。 または、省略記号 **[...]** をクリックして **[証明書の選択]** ダイアログ ボックスを開きます。 **[証明書名]** は、 **[ユーザーの種類]** で一覧から **[証明書にマップされたユーザー]** を選択した場合に使用できます。  
  
9. **[非対称キー名]**  ボックスに、データベース ユーザーに使用するキーを入力します。 または、省略記号 **[...]** をクリックして **[非対称キーの選択]** ダイアログ ボックスを開きます。 **[非対称キー名]** は、 **[ユーザーの種類]** で一覧から **[非対称キーにマップされたユーザー]** を選択した場合に使用できます。  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>追加オプション  
 **[データベース ユーザー - 新規]** ダイアログ ボックスでは、**[所有されているスキーマ]**、**[メンバーシップ]**、**[セキュリティ保護可能なリソース]**、**[拡張プロパティ]** という 4 つの追加ページにもオプションが提供されます。  
  
-   **[所有されているスキーマ]** ページには、新しいデータベース ユーザーが所有できるすべてのスキーマが一覧表示されます。 データベース ユーザーのスキーマを追加または削除するには、 **[このユーザーが所有するスキーマ]** で、スキーマの横のチェック ボックスをオンまたはオフにします。  
  
-   **[メンバーシップ]** ページには、新しいデータベース ユーザーが所有できるすべてのデータベース メンバーシップ ロールが一覧表示されます。 データベース ユーザーのロールを追加または削除するには、 **[データベース ロールのメンバーシップ]** で、ロールの横のチェック ボックスをオンまたはオフにします。  
  
-   **[セキュリティ保護可能なリソース]** ページには、すべてのセキュリティ保護可能なリソースと、ログインに付与できる、セキュリティ保護可能なリソースに対する権限が一覧表示されます。  
  
-   **[拡張プロパティ]** ページでは、カスタム プロパティをデータベース ユーザーに追加できます。 このページで使用できるオプションを次に示します。  
  
     **[データベース]**  
     選択しているデータベースの名前が表示されます。 このフィールドは読み取り専用です。  
  
     **Collation**  
     選択されているデータベースに使用する照合順序を表示します。 このフィールドは読み取り専用です。  
  
     **プロパティ**  
     オブジェクトの拡張プロパティを表示または指定します。 各拡張プロパティは、オブジェクトに関連付けられたメタデータの名前/値ペアで構成されています。  
  
     **省略記号 (...)**  
     **[値]** の後ろにある省略記号 **[...]** をクリックすると、**[拡張プロパティの値]** ダイアログ ボックスが開きます。 ここでは、より大きなテキスト ボックスを使用して拡張プロパティの値を入力または表示できます。 詳細については、「 [拡張プロパティの値ダイアログ ボックス](../../databases/value-for-extended-property-dialog-box.md)」を参照してください。  
  
     **削除**  
     選択されている拡張プロパティを削除します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-database-user"></a>データベース ユーザーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プリンシパル &#40;データベース エンジン&#41;](principals-database-engine.md)  
  
  
