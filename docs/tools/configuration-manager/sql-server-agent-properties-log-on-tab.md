---
title: SQL Server エージェントのプロパティ ([ログオン] タブ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: configuration-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f74928db1958fbb8ec607bac83b45612a6129e46
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MTE
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sql-server-agent-properties-log-on-tab"></a>[SQL Server Agent のプロパティ] ダイアログ ボックス ([ログオン] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
**[SQL Server Agent のプロパティ]** ダイアログ ボックスの **[ログオン]** タブでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスで使用するアカウントを指定します。また、このサービスの開始と停止も行えます。 アカウントのパスワードを変更した場合、サービスを再起動しなくても、すぐにその変更が有効になります。  
  
> [!NOTE]  
>  クラスター化されたインスタンス上のサービスで使用するアカウント名を変更する場合、新しいアカウントは、そのサービスのセットアップ時に指定したドメイン グループに属している必要があります。または、そのグループにメンバーを追加する権限が与えられている必要があります。 グループのメンバーシップを変更する権限がない場合は、ドメイン管理者に問い合わせてください。  
  
## <a name="options"></a>および  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。  
  
 **[このアカウント]**  
 Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
 **アカウント名**  
 ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。  
  
 **Password**  
 アカウントのパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 アカウントのパスワードを再度入力します。  
  
 **コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇**  
 サービスを開始します。  
  
 **[停止]**  
 サービスを停止します。  
  
 **[一時停止]**  
 サービスを一時停止します。  
  
 **[再開]**  
 一時停止したサービスを再開します。  
  
  
