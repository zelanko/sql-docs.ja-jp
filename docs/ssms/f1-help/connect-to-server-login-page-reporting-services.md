---
title: "[サーバーへの接続] ([ログイン] ページ) (Reporting Services) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttors.login.f1
helpviewer_keywords:
- Connect to Server dialog box, Reporting Services
ms.assetid: d312c740-19d7-4931-84a2-88b805ec8439
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f1dfb11e842436e8787624e3b16ba178423859b2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-login-page-reporting-services"></a>[サーバーへの接続] \([ログイン] ページ) (Reporting Services)
このタブは、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)] に接続するときに以下のオプションを表示または指定する場合に使用します。  
  
## <a name="options"></a>オプション  
**サーバーの種類**  
オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde_md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde_md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。  
  
**サーバー名**  
接続するレポート サーバー インスタンスのサーバー モードによって、入力する必要がある値が決まります。  
  
ネイティブ モードで実行されているレポート サーバーの場合、接続するレポート サーバー インスタンスを指定します。 既定のインスタンスを使用する場合、サーバー名はコンピューターの名前であるのが一般的です。 名前付きインスタンスをインストールしている場合は、 <servername>\\<InstanceName>の形式でサーバー名にインスタンス名を追加します。 Reporting Services では、円記号を使用してインスタンス名を区切ります。  
  
SharePoint 統合モードで実行されているレポート サーバーの場合、SharePoint サイトを指定する必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]と統合されているサイト コレクション内の任意のサイトを指定できます。 指定する URL には、HTTP プレフィックスまたは HTTPS プレフィックスを含める必要があります。 Management Studio で SharePoint サイトに接続するには、SharePoint サイトにアクセスする権限が必要です。 割り当てられている権限レベルによって、表示および管理できるアイテムが決まります。 詳細については、「 [レポート サーバーに登録および接続する方法](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e)」を参照してください。  
  
**[認証]**  
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)] を、指定したカスタム認証拡張機能によって処理する Windows 認証要求またはフォーム認証要求を受け入れるように構成できます。 Reporting Services に接続する際に、次のいずれかの認証モードを選択します。  
  
**Windows 認証モード ([Windows 認証])**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 資格情報を使用して、レポート サーバー インスタンスに接続します。  
  
**基本認証**  
Reporting Services をインストールしたときに、基本認証を使用するように構成している場合は、 **基本認証** を使用して接続します。  
  
**フォーム認証**  
Reporting Services をインストールしたときに、カスタム認証拡張機能を使用するように構成している場合は、 **フォーム認証** を使用して接続します。  
  
**[ユーザー名]**  
接続に使用するログイン名を入力します。 このオプションは、 **[基本認証]** または **[フォーム認証]**を選択した場合にのみ使用できます。  
  
**Password**  
ユーザー名に対応するパスワードを入力します。 このオプションは、 **[基本認証]** または **[フォーム認証]**を選択した場合にのみ編集できます。  
  
**[パスワードを保存する]**  
入力したパスワードを保存します。 このオプションは、 **[オプション]**をクリックした場合にのみ表示され、 **[基本認証]** または **[フォーム認証]**を使用して接続することにした場合にのみ編集できます。  
  
**Connect**  
選択されているサーバーに接続します。  
  
**オプション**  
パスワードの保存など、追加のサーバー接続オプションが表示されます。  
  
## <a name="see-also"></a>参照  
[レポート サーバー接続の構成](http://msdn.microsoft.com/en-us/9759a9fb-35e9-4215-969b-a9f1fea18487)  
[レポート サーバーに登録および接続する方法](http://msdn.microsoft.com/en-us/c875ff87-ee7d-443a-a702-bdb4b6c27c6e)  
[Reporting Services での認証の構成](http://msdn.microsoft.com/en-us/753c2542-0e97-4d8f-a5dd-4b07a5cd10ab)  
  

