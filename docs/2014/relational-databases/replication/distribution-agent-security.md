---
title: ディストリビューション エージェント セキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3e604ee6aac125f366ac2fca6444527340213019
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721495"
---
# <a name="distribution-agent-security"></a>[ディストリビューション エージェント セキュリティ]
  [**ディストリビューションエージェントセキュリティ**] ダイアログボックスを使用すると、ディストリビューションエージェントを実行する Windows アカウントを指定できます。 ディストリビューション エージェントは、プッシュ サブスクリプションのディストリビューターと、プル サブスクリプションのサブスクライバーで動作します。 エージェント プロセスはこのアカウントで実行されるため、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントは、 *プロセス アカウント*としても参照されます。 ダイアログ ボックスで使用できる追加オプションは、次に示すアクセスの方法によって異なります。  
  
-   サブスクリプションの新規作成ウィザードからこのダイアログ ボックスにアクセスする場合、サブスクライバー (プッシュ サブスクリプション) またはディストリビューター (プル サブスクリプション) への接続を作成するディストリビューション エージェントのコンテキストを指定することもできます。 接続は、Windows アカウントを借用するか、指定した[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アカウントのコンテキストで行うことができます。  
  
-   
  **[サブスクリプションのプロパティ]** ダイアログ ボックスからこのダイアログ ボックスにアクセスする場合、**[サブスクライバー接続]** 行または **[ディストリビューター接続]** 行のプロパティ ボタン ( **[...]** ) をクリックして、ディストリビューション エージェントが接続を作成するコンテキストを指定します。 
  **[サブスクリプションのプロパティ]** ダイアログ ボックスへのアクセスの詳細については、「[プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)」および「[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## <a name="options"></a>オプション  
 **プロセスアカウント**  
 ディストリビューション エージェントが実行される Windows アカウントを入力します。  
  
-   プッシュ サブスクリプションでは、アカウントには次のことが必要です。  
  
    -   少なくとも、ディストリビューションデータベースの**db_owner**固定データベースロールのメンバーである必要があります。  
  
    -   パブリケーション アクセス リスト (PAL) のメンバーになれる。  
  
    -   スナップショット共有の読み取り権限を持っている。  
  
    -   サブスクリプションが非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合、サブスクライバーの OLE DB プロバイダーのインストール ディレクトリへの読み取り権限を持つ。  
  
-   プル サブスクリプションでは、アカウントは少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
 接続を作成するときにプロセス アカウントを借用する場合、追加の権限が必要です。 後述の **[ディストリビューターに接続]** と **[サブスクライバーに接続]** を参照してください。  
  
 のインスタンスでディストリビューションエージェントが実行されて[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]いないため、の[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]プルサブスクリプションに対して**プロセスアカウント**を指定することはできません。  
  
 **パスワード**と**パスワードの確認入力**  
 Windows アカウントのパスワードを入力します。  
  
 **ディストリビューターへの接続**  
 プッシュ サブスクリプションでは、ディストリビューターへの接続は常に **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用することによって作成されます。  
  
 プル サブスクリプションでは、ディストリビューション エージェントが、 **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントを使用してディストリビューターへの接続を作成する必要があるかどうかを選択します。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
 接続に使用する Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントには次のことが必要です。  
  
-   PAL のメンバーである。  
  
-   スナップショット共有の読み取り権限を持っている。  
  
 **サブスクライバーへの接続**  
 プル サブスクリプションでは、サブスクライバーへの接続は常に **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用することによって作成されます。  
  
 プッシュ サブスクリプションでは、次のように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーと非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのオプションが異なります。  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーでは、ディストリビューション エージェントが、 **[プロセス アカウント]** テキスト ボックスに指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアカウントを使用してサブスクライバーへの接続を作成する必要があるかどうかを選択します。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
    > [!NOTE]  
    >  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
     サブスクライバーへの接続に使用される Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントは、少なくとも、サブスクリプション データベースの **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
-   非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーでは、ディストリビューション エージェントがサブスクライバーに接続するときに使用する必要のあるサブスクライバーでデータベース ログインを指定します。 ログインは、サブスクリプション データベースにオブジェクトを作成するための十分な権限を持つ必要があります。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバの詳細については、「[SQL Server 以外のサブスクライバーのサブスクリプションの作成](create-a-subscription-for-a-non-sql-server-subscriber.md)」を参照してください。  
  
 **追加の接続オプション**  
 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのみです。 接続文字列の形式で、サブスクライバーの任意の接続オプションを指定します (Oracle では追加のオプションは不要)。 各オプションはセミコロンで区切る必要があります。 次は、IBM DB2 接続文字列の例です (読みやすくするために改行されています)。  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 文字列内のオプションの多くは、接続する DB2 サーバーに固有のものですが、 **Process Binary as Character** オプションは常に **False**に設定する必要があります。 サブスクリプション データベースを識別するため、 **Initial Catalog** オプションに値が必要です。 詳細については、「 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーションでのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [レプリケーションエージェントのセキュリティモデル](security/replication-agent-security-model.md)   
 [レプリケーションエージェントの概要](agents/replication-agents-overview.md)   
 [レプリケーションのセキュリティに関するベストプラクティス](security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
