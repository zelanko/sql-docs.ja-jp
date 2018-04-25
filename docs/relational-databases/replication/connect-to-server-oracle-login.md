---
title: '[サーバーへの接続](Oracle)、[ログイン] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e4ab03d7c74d9e98da4c8141373a877aa485876
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-server-oracle-login"></a>[サーバーへの接続] \(Oracle)、[ログイン]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[サーバーへの接続]** ダイアログ ボックスの **[ログイン]** タブを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターから Oracle パブリッシャーへの接続を確立するためのアカウントを指定できます。 パブリッシャーの構成時にレプリケーション管理ユーザー スキーマ用に指定したものと同じアカウントを使用する必要があります。 詳細については、「[Configure an Oracle Publisher](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。  
  
## <a name="options"></a>および  
 **サーバー インスタンス**  
 ディストリビューターにインストールされた Oracle クライアント ソフトウェアの構成時に指定される、Oracle パブリッシャーの TNS (Transparent Network Substrate) 名です。  
  
 **[認証]**  
 **[Oracle 標準認証]** (推奨) または **[Windows 認証]** を選択してください。 **[Windows 認証]** を選択した場合 :  
  
-   Oracle サーバーは、Windows 資格情報を使用して接続を許可するように構成する必要があります。 詳細については Oracle のマニュアルを参照してください。  
  
-   現在、レプリケーション管理ユーザー スキーマ用に指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントと同じものを使用してログインしている必要があります。  
  
 **[ログイン]** と **[パスワード]**  
 **[認証]** オプションの **[Oracle 標準認証]** を選択した場合は、使用するログインとパスワードを指定してください。レプリケーション管理ユーザー スキーマに指定したものと同じである必要があります。  
  
## <a name="see-also"></a>参照  
 [Glossary of Terms for Oracle Publishing](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
