---
title: "登録済みサーバーまたは登録済みサーバー グループの名前の変更 | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying registered server or server group names
- server groups [SQL Server]
- Registered Servers [SQL Server], names
- renaming registered server or server group
- names [SQL Server], registered server or server group
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: b99eea0ee5988ce791948c2fa7340271b74e7ec4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>登録済みサーバーまたは登録済みサーバー グループの名前の変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、登録済みサーバーまたは登録済みサーバー グループの名前を変更する方法について説明します。 この名前はいつでも変更できます。 [登録済みサーバー] でサーバーの名前を変更すると、名前の表示のみが変更されます。 別のサーバーに接続するには、登録済みサーバーの接続プロパティを編集する必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
メニューから **[表示]\\[登録済みサーバー]** を選択し、**[登録済みサーバー]** ペインを開きます。  
#### <a name="to-change-the-name-of-a-server"></a>サーバーの名前を変更するには  
  
1.  **[登録済みサーバー]**の **[データベース エンジン]** 、 **[ローカル サーバー グループ]**の順に展開します。  

2.  サーバーを右クリックして **[プロパティ]** を選択し、 **[サーバー登録プロパティの編集]** ダイアログ ボックスを開きます。
  
3.  **[登録済みサーバーの名前]** テキスト ボックスにサーバーの新しい登録名を入力し、 **[保存]**をクリックします。  
  
#### <a name="to-change-the-name-of-a-server-group"></a>サーバー グループの名前を変更するには  
  
1.  **[登録済みサーバー]**の **[データベース エンジン]** 、 **[ローカル サーバー グループ]**の順に展開します。  

2.  サーバー グループを右クリックし、 **[プロパティ]** を選択して **[サーバー グループ プロパティの編集]** ダイアログ ボックスを開きます。 
  
3.  **[グループ名]** テキスト ボックスにサーバー グループの新しい名前を入力し、 **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [サーバーの登録の変更 &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)  
  
  

