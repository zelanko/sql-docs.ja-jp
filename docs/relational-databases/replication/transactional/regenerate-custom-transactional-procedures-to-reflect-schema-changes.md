---
title: "カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カスタム プロシージャ [SQL Server レプリケーション]"
  - "トランザクション レプリケーション, スキーマ変更のレプリケート"
  - "スキーマ [SQL Server レプリケーション], 変更のレプリケート"
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映
  既定では、トランザクション レプリケーションがサブスクライバー上のデータを変更する際、パブリケーション内の各テーブル アーティクルに対して内部プロシージャが生成したストアド プロシージャが必ず使われます。 3 つのプロシージャ (挿入、更新、削除用に 1 つずつ) はサブスクライバーにコピーされ、挿入、更新、削除がサブスクライバーにレプリケートされた時点で実行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャー上のテーブルでスキーマが変更されると、レプリケーションがスクリプト作成内部プロシージャの同じセットを呼び出すことで、これらのプロシージャが自動的に再生成され、新しいプロシージャと新しいスキーマが一致します (スキーマ変更のレプリケーションは、Oracle パブリッシャーではサポートされていません)。  
  
 カスタム プロシージャを指定して、1 つ以上の既定のプロシージャを置き換えることもできます。 スキーマ変更によってカスタム プロシージャが影響を受ける場合は、そのプロシージャを変更する必要があります。 たとえば、スキーマ変更によって削除される列をプロシージャが参照している場合には、その列への参照をプロシージャから削除する必要があります。 レプリケーションで新しいカスタム プロシージャをサブスクライバーに反映するには、2 つの方法があります。  
  
-   1 つ目のオプションは、カスタム スクリプト作成プロシージャを使用して、レプリケーションで使用する既定のプロシージャを置き換える方法です。  
  
    1.  実行時に [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), 、確認、 **@schema_option** 0x02 ビット **true**します。  
  
    2.  実行 [sp_register_custom_scripting & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) 'insert'、'update'、または 'delete' のパラメーターの値を指定して **@type** とカスタムの名前がパラメーターのプロシージャをスクリプト **@value**します。  
  
     次回にスキーマが変更されると、レプリケーションによってこのストアド プロシージャが呼び出され、新しくユーザーが定義したカスタム ストアド プロシージャの定義がスクリプト化されて、プロシージャが各サブスクライバーに反映されます。  
  
-   2 つ目のオプションは、新しいカスタム プロシージャの定義を含むスクリプトを使用する方法です。  
  
    1.  実行時に [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), 、設定、 **@schema_option** 0x02 ビットに **false** レプリケーションがサブスクライバーでのカスタム プロシージャを自動的に生成しないようにします。  
  
    2.  各スキーマ変更の前に新しいスクリプト ファイルを作成し、レプリケーションを実行して、スクリプトを登録 [sp_register_custom_scripting & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)します。 'Custom_script' パラメーターの値を指定して **@type** とパラメーターにパブリッシャー上のスクリプトへのパス **@value**します。  
  
     次回に関連スキーマが変更されると、各サブスクライバーでは、DDL コマンドと同じトランザクション内でこのスクリプトが実行されます。 スキーマ変更が完了すると、スクリプトの登録が解除されます。 以降のスキーマ変更でこのスクリプトを実行するには、スクリプトを再登録する必要があります。  
  
## 参照  
 [トランザクション アーティクルに変更を反映する方法の指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  