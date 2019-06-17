---
title: 接続済みのサーバーの登録 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 80dbd927f0a1b008e48fda7fcbd4a7e75b7fbaf8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191941"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>接続済みのサーバーの登録 (SQL Server Management Studio)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサーバーを登録する方法について説明します。 サーバーを登録することによって、頻繁にアクセスするサーバーの接続情報を保存しておくことができます。 サーバーの登録は、接続する前か、またはオブジェクト エクスプローラーから接続するときに実行できます。  
  
 **このトピックの内容**  
  
-   **サーバーを登録する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-register-a-connected-server"></a>接続済みのサーバーを登録するには  
  
1.  オブジェクト エクスプローラーで、接続済みのサーバーを右クリックし、 **[登録]** をクリックします。  
  
     **サーバー名**  
     登録するサーバーに使用する名前を入力します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してローカル サーバーまたはリモート サーバーを登録することにより、以降の接続で使用するサーバー接続情報を格納できます。 このフィールドの既定値は、サーバーに接続したときに入力したサーバー名です。 このサーバー名を維持するか、別の使いやすい名前を入力します。  
  
     **サーバーの説明**  
     サーバーの説明をオプションで入力します。 最大 250 文字以内で指定します。  
  
     **サーバー グループを選択します。**  
     サーバー登録を保存するサーバー グループを選択します。  
  
     **[新しいグループ]**  
     クリックすると、登録するサーバー用の新しいサーバー グループを作成するための **[新しいグループ]** ダイアログ ボックスが開きます。  
  
     **および**  
     クリックすると、入力した情報を保存して登録済みサーバーを作成できます。  
  
  
