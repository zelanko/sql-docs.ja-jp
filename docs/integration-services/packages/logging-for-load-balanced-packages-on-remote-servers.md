---
title: "リモート サーバー上の負荷分散パッケージのログ記録 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ [Integration Services], リモート パッケージ"
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# リモート サーバー上の負荷分散パッケージのログ記録
  すべての子パッケージで同じログ プロバイダーを使用し、これらの出力先を同じにすれば、さまざまなサーバーで実行されているすべての子パッケージに関するログの管理が容易になります。 すべての子パッケージに共通するログ ファイルを作成する方法の 1 つとして、イベントのログが SQL Server ログ プロバイダーに記録されるように子パッケージを構成することができます。 すべてのパッケージが、同じデータベース、同じサーバー、同じサーバー インスタンスを使用するように構成できます。  
  
 管理者は、1 台のサーバーにログオンするだけで、すべての子パッケージに関するログ ファイルを確認できます。  
  
## 関連タスク  
 パッケージでログ記録を有効にする方法については、「[SQL Server Data Tools でパッケージのログ記録を有効にする](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)」を参照してください。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  