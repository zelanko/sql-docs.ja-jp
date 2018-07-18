---
title: HOST_NAME 値 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 08aa004ddbece8e40739ef42d847852731f643b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190029"
---
# <a name="hostname-values"></a>[HOST_NAME 値]
  パラメーター化されたフィルター付きのマージ パブリケーションは、SUSER_SNAME() 関数または HOST_NAME() 関数を使用してデータにフィルターをかけます。 関数は、パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ]** ダイアログ ボックスで指定します。  
  
 既定では、HOST_NAME() 関数は、パブリッシャーに接続しているコンピューターの名前を返します。 通常、パラメーター化されたフィルターを使用する場合は、ウィザードのこのページで値を指定してこの値をオーバーライドします。 これにより、HOST_NAME() 関数は、コンピューターの名前ではなく、指定された値を返します。 詳細については、「[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)」 (パラメーター化された行フィルター) の "Overriding the HOST_NAME() Value" (HOST_NAME() 値のオーバーライド) をご覧ください。  
  
> [!NOTE]  
>  HOST_NAME() をオーバーライドした場合、HOST_NAME() 関数のすべての呼び出しは、指定された値を返します。 他のアプリケーションが、コンピューター名を返す HOST_NAME() 関数に依存していないことを確認してください。  
  
## <a name="options"></a>および  
 **[サブスクリプションのプロパティ]**  
 サブスクライバーごとに **[HOST_NAME 値]** 列に値を入力するか、既定値を受け入れます。既定値は、サブスクライバー コンピューターの名前です。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
