---
title: '[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22c365dfd5a6c6fd38e256821a6dd80ff99345fd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48195162"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ)
  **のプロパティ** ダイアログ ボックスの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **[ログオン]** タブでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが使用するアカウントの指定や、そのサービスの開始、停止を行います。  
  
## <a name="options"></a>および  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。  
  
 **[このアカウント]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を検索してください。  
  
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
  
  
