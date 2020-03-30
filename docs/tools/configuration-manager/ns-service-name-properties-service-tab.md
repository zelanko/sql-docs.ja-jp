---
title: NS$&lt;サービス名&gt; プロパティ ([サービス] タブ)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 57c6b791-1663-4a01-9de2-cf1bdd8adb2c
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 80f6d926dbe1380bf0f44b8b841d79b2bd66afc7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306392"
---
# <a name="nsltservice-namegt-properties-service-tab"></a>NS$&lt;サービス名&gt; プロパティ ([サービス] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  このサービスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNS](../../includes/ssns-md.md)] サービスです。 グレー表示になっているプロパティ値をこのアプリケーションで変更することはできません。  
  
## <a name="options"></a>オプション  
 **[バイナリ パス]**  
 このサービスが使用するプログラム ファイルの場所が表示されます。  
  
 **[エラー制御]**  
 1 は `SERVICE_ERROR_NORMAL`を示します。 コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。 この値は変更できません。  
  
 **終了コード**  
 エラーが発生した場合は、エラー番号がこのボックスに表示されます。 その番号を手掛かりにして障害のトラブルシューティングを行ってください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート技術情報でその番号を検索することも、技術サポート スタッフにその番号を連絡することも可能です。  
  
 **Host Name**  
 フルテキスト検索を実行しているコンピューターまたはクラスターの名前が表示されます。  
  
 **Name**  
 サービスの表示名が表示されます。  
  
 **プロセス ID**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows プロセス ID が表示されます。  
  
 **[SQL サービスの種類]**  
 呼び出し側プロセスに提供されるサービスの種類です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いくつかのサービスがインストールされます。  
  
 **[開始モード]**  
 このサービスを以下のいずれかのモードに設定します。  
  
-   手動: このサービスは、コンピューターの起動時に自動的に開始しません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。  
  
-   \[自動]: このサービスは、コンピューターの起動時に開始を試みます。  
  
-   \[無効]: このサービスは開始できません。  
  
 **State**  
 このサービスが実行中か、停止しているか、無効になっているかが表示されます。  
  
  
