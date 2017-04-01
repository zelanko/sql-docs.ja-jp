---
title: "[HOST_NAME 値] | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.hostnamevalue.f1"
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# [HOST_NAME 値]
  パラメーター化されたフィルター付きのマージ パブリケーションは、SUSER_SNAME() 関数または HOST_NAME() 関数を使用してデータにフィルターをかけます。 関数は、パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ]** ダイアログ ボックスで指定します。  
  
 既定では、HOST_NAME() 関数は、パブリッシャーに接続しているコンピューターの名前を返します。 通常、パラメーター化されたフィルターを使用する場合は、ウィザードのこのページで値を指定してこの値を上書きします。 これにより、HOST_NAME() 関数は、コンピューターの名前ではなく、指定された値を返します。 詳細については、の「HOST_NAME() 値のオーバーライド」セクションを参照してください。 [パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
> [!NOTE]  
>  HOST_NAME() を上書きした場合、HOST_NAME() 関数のすべての呼び出しは、指定された値を返します。 他のアプリケーションが、コンピューター名を返す HOST_NAME() 関数に依存していないことを確認してください。  
  
## オプション  
 **[サブスクリプションのプロパティ]**  
 サブスクライバーごとに値を入力、 **HOST_NAME 値** 列か、既定では、サブスクライバー コンピューターの名前を指定します。  
  
## 参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME & #40 です。Transact SQL と #41 です。](../../t-sql/functions/host-name-transact-sql.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  