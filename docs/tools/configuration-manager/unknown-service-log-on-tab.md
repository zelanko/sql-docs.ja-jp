---
title: '[不明なサービス] ダイアログ ボックス ([ログオン] タブ)'
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8fae62bb72e41cd9f87200a6bcfd2f17eb780697
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307591"
---
# <a name="unknown-service-log-on-tab"></a>[不明なサービス] ダイアログ ボックス ([ログオン] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、このサービスを識別できません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、サービスを実行しているコンピューターの WMI プロバイダーからそのサービスの情報を受け取ります。 そのサービスのプロパティの読み取り中にエラーが発生したか、そのサービスのプロパティに不備がありました。 この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーをいったん閉じてから再び開くか、そのサービスを実行しているコンピューターの WMI プロバイダーをチェックします。  
  
 WMI プロバイダーは、Windows のコンポーネントです。 WMI プロバイダーのアクセス許可を確認する方法については、SQL Server オンライン ブックの「操作方法: SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成」を参照してください。  
  
 適切なサービスを表示していると確信できる場合は、 **[不明なサービス]** ダイアログ ボックスの **[ログオン]** タブで、そのサービスが使用するアカウントの指定や、そのサービスの開始と停止を行います。  
  
## <a name="options"></a>オプション  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントを指定します。このアカウントはパスワードを必要としません。 ただし、ローカル システム アカウントに与えられている特権によっては、そのサービスが他のサーバーと対話できないこともあります。  
  
 **[このアカウント]**  
 Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
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
  
  
