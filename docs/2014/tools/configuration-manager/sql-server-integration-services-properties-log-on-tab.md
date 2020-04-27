---
title: '[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bcaa38cd3849f1665d0f31e8d2749730d2494fcc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63217946"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([ログオン] タブ)
  [ **の**プロパティ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]] ダイアログ ボックスの **[ログオン]** タブでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスで使用するアカウントの指定や、そのサービスの開始、停止を行います。  
  
## <a name="options"></a>オプション  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスと他のサーバーとの対話が制限されることもあります。  
  
 **[このアカウント]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を検索してください。  
  
 **アカウント名**  
 ローカル ユーザー アカウント名またはドメイン ユーザー アカウント名を指定します。  
  
 **パスワード**  
 アカウントのパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 アカウントのパスワードを再度入力します。  
  
 **[開始]**  
 サービスを開始します。  
  
 **Stop**  
 サービスを停止します。  
  
 **[一時停止]**  
 サービスを一時停止します。  
  
 **[再開]**  
 一時停止したサービスを再開します。  
  
  
