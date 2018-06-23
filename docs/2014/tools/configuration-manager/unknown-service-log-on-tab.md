---
title: 不明なサービス ([ログオン] タブ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7c69029b006c4fde006a83a8849e104cc5a74ea2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084213"
---
# <a name="unknown-service-log-on-tab"></a>[不明なサービス] ダイアログ ボックス ([ログオン] タブ)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、このサービスを識別できません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、サービスを実行しているコンピューターの WMI プロバイダーからそのサービスの情報を受け取ります。 そのサービスのプロパティの読み取り中にエラーが発生したか、そのサービスのプロパティに不備がありました。 この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーをいったん閉じてから再び開くか、そのサービスを実行しているコンピューターの WMI プロバイダーをチェックします。  
  
 WMI プロバイダーは、Windows のコンポーネントです。 WMI プロバイダーの権限をチェックする方法については、SQL Server オンライン ブックの「SQL Server ツールでサーバーの状態を表示できるように WMI を構成する方法」を参照してください。  
  
 適切なサービスを表示していると確信できる場合は、 **[不明なサービス]** ダイアログ ボックスの **[ログオン]** タブで、そのサービスが使用するアカウントの指定や、そのサービスの開始と停止を行います。  
  
## <a name="options"></a>および  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。  
  
 **[このアカウント]**  
 Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
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
  
  