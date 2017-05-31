---
title: "Web サーバー情報 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9c3db680206fb7c752fe27f968961d751c78aae0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="web-server-information"></a>Web サーバー情報
  Web サーバー情報は、マージ レプリケーションの Web 同期オプションを使用する場合に必要です。 Web 同期の構成の詳細については、「[Configure Web Synchronization (Web 同期の構成)](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **[Web サーバー アドレス]**  
 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[FTP スナップショットとインターネット]** ページで Web サーバー アドレスを指定している場合は、そのアドレスがこのテキスト ボックスに既定として表示されます。 既定値を受け入れるか、このサブスクリプションを同期する [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) の完全修飾 Web サーバー アドレスを入力します。  
  
 **[各サブスクライバーが Web サーバーに接続する方法を指定します。]**  
 Web サーバーへの接続に使用される認証の種類を指定します。 IIS サーバーへの接続用の [基本認証] を SSL (Secure Sockets Layer) と組み合わせて使用することをお勧めします。 [基本認証] を選択した場合は、サブスクライバーから IIS サーバーへの接続に使用されるログインとパスワードを入力してください。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [プル サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
