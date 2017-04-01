---
title: "パスワード ポリシー | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "09/25/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ALTER LOGIN ステートメント"
  - "パスワード [SQL Server]、ポリシーの適用"
  - "ログイン [SQL Server]、パスワード"
  - "CHECK_EXPIRATION オプション"
  - "複雑なパスワード [SQL Server]"
  - "パスワード [SQL Server]、有効期限切れ"
  - "手動による不正なパスワード カウントのリセット"
  - "MUST_CHANGE オプション"
  - "有効期限 [SQL Server]"
  - "期限切れのパスワード [SQL Server]"
  - "記号 [SQL Server]"
  - "NetValidatePasswordPolicy() API"
  - "パスワード [SQL Server]"
  - "パスワード ポリシー [SQL Server]"
  - "不正なパスワード カウントのリセット"
  - "セキュリティ [SQL Server]、パスワード"
  - "CHECK_POLICY オプション"
  - "パスワード [SQL Server]、シンボル"
  - "不正なパスワード カウント"
  - "パスワード [SQL Server]、複雑性"
  - "文字 [SQL Server]、パスワード ポリシー"
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# パスワード ポリシー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows のパスワード ポリシー メカニズムに対応しています。 パスワード ポリシーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するログインに適用され、パスワードを持つ包含データベース ユーザーに適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部で使用されるパスワードに、Windows で使用されているものと同じ複雑性ポリシーおよび有効期限ポリシーを適用できます。 この機能は `NetValidatePasswordPolicy` API に依存します。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] パスワードの複雑性が適用されます。 パスワードの有効期限とポリシー適用のセクションは [!INCLUDE[ssSDS](../../includes/sssds-md.md)] に適用されません。  
  
## パスワードの複雑性  
 パスワードの複雑性のポリシーは、使用可能なパスワードの数を増やすことにより、総当り攻撃を防ぐようにデザインされています。 パスワードの複雑性のポリシーが適用される場合、新しいパスワードは次のガイドラインを満たしている必要があります。  
  
-   パスワードはユーザー アカウント名を含まない。  
  
-   パスワードは 8 文字以上である。  
  
-   パスワードは次の 4 つのカテゴリのうちの 3 つのカテゴリの文字を含む。  
  
    -   ラテン文字の大文字 (A ～ Z)  
  
    -   ラテン文字の小文字 (a ～ z)  
  
    -   算用数字 (0 ～ 9)  
  
    -   感嘆符 (!)、ドル記号 ($)、番号記号 (#)、パーセント記号 (%) などの英数字以外の文字  
  
 パスワードには最大 128 文字まで使用できます。 パスワードはできるだけ長く、複雑にすることをお勧めします。  
  
## パスワードの有効期限  
 パスワードの有効期限のポリシーは、パスワードの寿命を管理します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってパスワードの有効期限が適用されている場合、ユーザーは古いパスワードを変更するよう通知され、有効期限が切れたパスワードを持つアカウントは無効になります。  
  
## ポリシーの適用  
 パスワード ポリシーの適用は、SQL Server ログインごとに個別に構成できます。 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md) を使用して、SQL Server ログインのパスワード ポリシー オプションを構成します。 パスワード ポリシーの適用を構成する際に、次の規則が当てはまります。  
  
-   CHECK_POLICY を ON に変更した場合、次の動作が行われます。  
  
    -   CHECK_EXPIRATION も、明示的に OFF に設定されない限り、ON に設定されます。  
  
    -   パスワードの履歴が、現在のパスワード ハッシュの値に初期化されます。  
  
    -   **[アカウント ロックアウトの期間]**、**[アカウント ロックアウトのしきい値]**、および **[ロックアウト カウンターのリセット]** も有効になります。  
  
-   CHECK_POLICY を OFF に変更した場合、次の動作が行われます。  
  
    -   CHECK_EXPIRATION も OFF に設定されます。  
  
    -   パスワード履歴は消去されます。  
  
    -   `lockout_time` の値がリセットされます。  
  
 ポリシー オプションの組み合わせには、サポートされないものがあります。  
  
-   MUST_CHANGE が指定された場合、CHECK_EXPIRATION および CHECK_POLICY は ON に設定されなければなりません。 ON に設定しない場合、ステートメントは失敗します。  
  
-   CHECK_POLICY を OFF に設定した場合、CHECK_EXPIRATION を ON に設定することはできません。 このオプションの組み合わせで ALTER LOGIN ステートメントを実行すると、ステートメントは失敗します。  
  
 CHECK_POLICY = ON を設定すると、次のようなパスワードは作成できなくなります。  
  
-   NULL または空文字列  
  
-   コンピューター名またはログイン名と同じ文字列  
  
-   "password"、"admin"、"administrator"、"sa"、"sysadmin" のいずれかの文字列  
  
 セキュリティ ポリシーは、Windows で設定する場合も、ドメインから受け取る場合もあります。 コンピューターでパスワード ポリシーを表示するには、ローカル セキュリティ ポリシーの MMC スナップイン (**secpol.msc**) を使用します。  
  
## 関連タスク  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)  
  
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)  
  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)  
  
 [ALTER USER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-user-transact-sql.md)  
  
 [ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)  
  
 [データベース ユーザーの作成](../../relational-databases/security/authentication-access/create-a-database-user.md)  
  
## 関連コンテンツ  
 [強力なパスワード](../../relational-databases/security/strong-passwords.md)  
  
  